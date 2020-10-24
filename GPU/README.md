# cgpu optimizations

### amd

##### 5700xt

###### Defaults

OD_SCLK:
0: 800Mhz
1: 2009Mhz
OD_MCLK:
1: 875MHz
OD_VDDC_CURVE:
0: 800MHz @ 708mV
1: 1404MHz @ 833mV
2: 2009MHz @ 1194mV
OD_RANGE:
SCLK:     800Mhz       2150Mhz
MCLK:     625Mhz        950Mhz
VDDC_CURVE_SCLK[0]:     800Mhz       2150Mhz
VDDC_CURVE_VOLT[0]:     750mV        1200mV
VDDC_CURVE_SCLK[1]:     800Mhz       2150Mhz
VDDC_CURVE_VOLT[1]:     750mV        1200mV
VDDC_CURVE_SCLK[2]:     800Mhz       2150Mhz
VDDC_CURVE_VOLT[2]:     750mV        1200mV


dual

```
overclock() {
        set -x
        i=0
        echo "manual" >  /sys/class/drm/card$i/device/power_dpm_force_performance_level
        echo "2" >  /sys/class/drm/card$i/device/pp_dpm_sclk
        echo "3" >  /sys/class/drm/card$i/device/pp_dpm_mclk
        echo "s 1 1350" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "m 1 920" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 0 1250 750" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 1 1250 750" >  /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 2 1250 750" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        #echo "vc 0 1150 750" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        #echo "vc 1 1250 751" >  /sys/class/drm/card$i/device/pp_od_clk_voltage
        #echo "vc 2 1300 752" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "c" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "1" > /sys/class/drm/card$i/device/hwmon/hwmon*/pwm1_enable
        echo "255" > /sys/class/drm/card$1/device/hwmon/hwmon*/pwm1


        i=1
        echo "manual" >  /sys/class/drm/card$i/device/power_dpm_force_performance_level
        echo "2" >  /sys/class/drm/card$i/device/pp_dpm_sclk
        echo "3" >  /sys/class/drm/card$i/device/pp_dpm_mclk
        echo "s 1 1300" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "m 1 920" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 0 1300 750" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 1 1300 750" >  /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 2 1300 750" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        #echo "vc 0 1150 750" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        #echo "vc 1 1200 751" >  /sys/class/drm/card$i/device/pp_od_clk_voltage
        #echo "vc 2 1300 752" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "c" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "1" > /sys/class/drm/card$i/device/hwmon/hwmon*/pwm1_enable
        echo "255" > /sys/class/drm/card$1/device/hwmon/hwmon*/pwm1
        set +x
}
overclock
```


pc

```

MEM_CLK=910
CORE_CLK=1300

overclock() {
        set -x
        i=0
        echo "manual" >  /sys/class/drm/card$i/device/power_dpm_force_performance_level
        echo "s 1 $CORE_CLK" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "m 1 $MEM_CLK" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 0 800 680" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 1 1100 685" >  /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 2 1400 825" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "vc 2 1300 760" > /sys/class/drm/card$i/device/pp_od_clk_voltage
        echo "c" > /sys/class/drm/card$i/device/pp_od_clk_voltage
}

overclock
```
