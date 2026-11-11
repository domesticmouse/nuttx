# NuttX Sensor & uORB Subsystem (`include/nuttx/sensors`)

## Overview
Defines the NuttX Sensor upper-half/lower-half framework (`sensor.h`), GNSS receiver abstraction (`gnss.h`), quadrature encoder (`qencoder.h`), zero-cross detector (`zerocross.h`), 3-phase Hall effect sensor (`hall3ph.h`), sensor cluster driver (`cluster_driver.h`), standard `SNIOC_*` ioctls (`ioctl.h`), and over 100 hardware sensor driver registration interfaces (IMUs, accelerometers, gyroscopes, magnetometers, barometers, environmental/gas sensors, optical/ToF sensors, current/power monitors, and thermocouple/temperature sensors).

## Interface
- `sensor.h:sensor_lowerhalf_s`, `sensor.h:sensor_ops_s`, `sensor.h:sensor_push_event_t`, `sensor.h:sensor_notify_event_t`, `sensor.h:sensor_register`, `sensor.h:sensor_custom_register`, `sensor.h:sensor_unregister`, `sensor.h:sensor_custom_unregister`, `sensor.h:usensor_initialize`, `sensor.h:sensor_rpmsg_register`, `sensor.h:sensor_get_timestamp`, `sensor.h:sensor_remap_vector_raw16` - Core uORB/sensor upper-half registration, lower-half vtable (`open`, `close`, `activate`, `set_interval`, `batch`, `fetch`, `flush`, `selftest`, `set_calibvalue`, `calibrate`, `get_info`, `set_nonwakeup`, `control`), coordinate remapping (`SENSOR_BODY_COORDINATE_P0`..`P7`), and RPMsg proxy registration.
- `ioctl.h:SNIOC_ENABLE`, `ioctl.h:SNIOC_DISABLE`, `ioctl.h:SNIOC_CONFIGURE`, `ioctl.h:SNIOC_SET_INTERVAL`, `ioctl.h:SNIOC_BATCH`, `ioctl.h:SNIOC_FLUSH`, `ioctl.h:SNIOC_SELFTEST`, `ioctl.h:SNIOC_GET_INFO` - Standard sensor character driver ioctl commands.
- `gnss.h:gnss_lowerhalf_s`, `gnss.h:gnss_ops_s`, `gnss.h:gnss_register`, `gnss.h:gnss_unregister`, `cxd5610_gnss.h:cxd5610_gnss_register`, `goldfish_gnss.h:goldfish_gnss_init`, `l86xxx.h:l86xxx_register` - GNSS upper/lower-half abstraction and hardware receivers.
- `qencoder.h:qe_lowerhalf_s`, `qencoder.h:qe_ops_s`, `qencoder.h:qe_register`, `qencoder.h:QEIOC_POSITION`, `qencoder.h:QEIOC_RESET`, `as5048a.h:as5048a_initialize`, `as5048b.h:as5048b_initialize`, `mt6816.h:mt6816_initialize` - Quadrature and magnetic rotary position encoder interfaces.
- `hall3ph.h:hall3_lowerhalf_s`, `hall3ph.h:hall3_ops_s`, `hall3ph.h:hall3_register`, `zerocross.h:zc_lowerhalf_s`, `zerocross.h:zc_register`, `cluster_driver.h:sensor_cluster_operations_s` - 3-phase Hall sensor, AC zero-crossing, and multi-sensor SPI/I2C cluster interfaces.
- Representative IMU/Motion/Environmental/Power/Optical device headers: `bmi160.h:bmi160_register`, `bmi270.h:bmi270_register`, `bmi088.h:bmi088_acc_register`, `lsm6dsl.h:lsm6dsl_sensor_register`, `lsm6dso32.h:lsm6dso32_register`, `mpu60x0.h:mpu60x0_register`, `mpu9250.h:mpu9250_register`, `bme680.h:bme680_register`, `bmp280.h:bmp280_register`, `sht3x.h:sht3x_register`, `scd41.h:scd41_register_i2c`, `ina219.h:ina219_register`, `ina226.h:ina226_register`, `vl53l1x.h:vl53l1x_register`, `fakesensor.h:fakesensor_init`, `goldfish_sensor.h:goldfish_sensor_init`.

## Invariants
- In `sensor.h:sensor_lowerhalf_s`, if `ops->fetch` is non-NULL, the upper-half disables its internal circular buffer (`nbuffer` is ignored for buffering) and the lower-half must use `notify_event` rather than `push_event`.
- Calling `ops->batch` in `sensor.h:sensor_ops_s` requires a sampling interval to have been configured first via `ops->set_interval` (otherwise `-EINVAL` is returned), and any queued FIFO samples must be pushed before changing latency so no measurements are lost.
- Asynchronous `ops->flush` implementations in `sensor.h:sensor_ops_s` must invoke `push_event(priv, NULL, 0)` upon completion to signal `POLLPRI` to waiting subscribers.

## Side Effects
- `sensor.h:sensor_register`, `sensor.h:sensor_custom_register`, `gnss.h:gnss_register`, and `qencoder.h:qe_register` allocate upper-half state and circular buffers, register `/dev/uorb/*` or `/dev/snsr*` character nodes, and bind lower-half `push_event`/`notify_event` callbacks.
- Lower-half driver operations (`activate`, `fetch`, `selftest`, `calibrate`) perform I2C/SPI/1-Wire bus transactions and configure GPIO interrupts on physical sensor ICs.

## Verification
- Run: `make test`
