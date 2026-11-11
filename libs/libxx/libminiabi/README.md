<Minimal C++ ABI Runtime (`libs/libxx/libminiabi`)>
## Overview
Provides a lightweight, freestanding C++ ABI runtime (`libminiabi`) for embedded NuttX targets that do not link a full external C++ runtime (`libsupc++` or `libc++abi`). It implements dynamic memory allocation/deallocation operators (`new`, `new[]`, `delete`, `delete[]`), one-time static local initialization guards (`__cxa_guard_*`), pure virtual call traps (`__cxa_pure_virtual`), and Itanium C++ ABI RTTI / `dynamic_cast` support (`std::type_info`, `__cxxabiv1::*`, `__dynamic_cast`).

## Interface
- `libxx_new.cxx:operator new` and `libxx_newa.cxx:operator new[]` - Heap allocation and placement-new operators backed by `lib_malloc`.
- `libxx_delete.cxx:operator delete` and `libxx_deletea.cxx:operator delete[]` - Unsized and C++14 sized (`CONFIG_HAVE_CXX14`) deallocation operators backed by `lib_free`.
- `libxx_cxa_guard.cxx:__cxa_guard_acquire`, `libxx_cxa_guard.cxx:__cxa_guard_release`, `libxx_cxa_guard.cxx:__cxa_guard_abort` - Itanium/ARM EABI (`__ARM_EABI__`) static initialization guard primitives.
- `libxx_cxapurevirtual.cxx:__cxa_pure_virtual` - Pure virtual function call handler that triggers `DEBUGPANIC()`.
- `libxx_typeinfo.h:std::type_info`, `libxx_typeinfo.h:__cxxabiv1::__class_type_info`, `libxx_typeinfo.h:__cxxabiv1::__si_class_type_info`, `libxx_typeinfo.h:__cxxabiv1::__base_class_type_info`, `libxx_typeinfo.h:__cxxabiv1::__vmi_class_type_info` - Standard and Itanium ABI single/virtual/multiple inheritance type information classes implemented in `libxx_typeinfo.cxx` and `libxx_dynamic_cast.cxx`.
- `libxx_dynamic_cast.cxx:__dynamic_cast` - Runtime polymorphic downcasting/crosscasting entry point enabled when `CONFIG_CXX_RTTI` is defined.

## Invariants
- `libxx_new.cxx:operator new` and `libxx_newa.cxx:operator new[]` enforce non-NULL allocation returns (`DEBUGASSERT(alloc != NULL)`) and non-NULL placement pointers (`DEBUGASSERT(ptr != NULL)`), treating zero-byte allocation requests as 1 byte (`nbytes < 1`).
- `libxx_typeinfo.h:std::type_info` preserves the vtable slot ordering of `libsupc++` (`~type_info`, `__is_pointer_p`, `__is_function_p`, `__do_catch`, `__do_upcast`) for ABI compatibility.

## Side Effects
- `libxx_new.cxx:operator new` and `libxx_newa.cxx:operator new[]` allocate heap memory via `lib_malloc` and emit error diagnostics via `_err` when `CONFIG_DEBUG_ERROR` is enabled.
- `libxx_delete.cxx:operator delete` and `libxx_deletea.cxx:operator delete[]` free heap memory via `lib_free`.
- `libxx_cxapurevirtual.cxx:__cxa_pure_virtual` halts or panics the task/system via `DEBUGPANIC()`.
- `libxx_cxa_guard.cxx:__cxa_guard_release` mutates the static guard variable `*g` to `1`.

## Verification
- Run: `make test`
</Minimal C++ ABI Runtime (`libs/libxx/libminiabi`)>
