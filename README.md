# Clas Clara Engine

Clas12 specific framework to design Clara service engines. Supports
developing engines for data processing, data analyses and data monitoring
services.

### Clara YAML configuration support

```
io-services:
  reader:
    class: org.jlab.clas.std.services.convertors.HipoToHipoReader
    name: HipoToHipoReader
  writer:
    class: org.jlab.clas.std.services.convertors.HipoToHipoWriter
    name: HipoToHipoWriter
services:
  data-processing:
    chain:
     - class: org.jlab.clara.clas12.dc.reconstruction.VDCHBEngine
       name: DCHB
#     - class: org.jlab.service.dc.DCTBEngine
#       name: DCTB
  monitoring:
    chain:
     - class: org.jlab.clara.clas12.dc.monitor.DcMonitorEngine
       name: DCMON

mime-types:
  - binary/data-hipo

configuration:
  global:
    magnet:
      torus: -1
      solenoid: 1
    ccdb:
      run: 101
      variation: custom
    runtype: mc
    runmode: calibration

  io-services:
    writer:
      compression: 2

  services:
    DCMON:
      log: true
      vvar: 1371
      kalman: true
```