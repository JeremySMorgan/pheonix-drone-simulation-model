

launch gazebo:
--------------

gazebo --verbose typhoon_ardupilot.world




launch sitl/ardupilot:
----------------------
sv -f Gazebo -v ArduCopter --map --console

 sv -f Gazebo -v ArduCopter --map --console


sv -v ArduCopter -f hexa --add-param-file="./Tools/autotest/default_params/copter-hexa.parm"




commands - see https://ardupilot.org/dev/docs/copter-sitl-mavproxy-tutorial.html
--------


mode guided
arm throttle
takeoff 2


# optional
param load Tools/autotest/default_params/motherdrone.parm












sim vehichle help:

Usage: sim_vehicle.py

Options:
  -h, --help            show this help message and exit
  -v VEHICLE, --vehicle=VEHICLE
                        vehicle type
                        (AntennaTracker|ArduPlane|ArduSub|Rover|ArduCopter)
  -f FRAME, --frame=FRAME
                        set vehicle frame type
                        AntennaTracker: tracker
                        ArduPlane: CRRCSim|calibration|firefly|gazebo-
                            zephyr|jsbsim|last_letter|plane|plane-
                            dspoilers|plane-elevon|plane-jet|plane-
                            soaring|plane-tailsitter|plane-
                            vtail|quadplane|quadplane-cl84|quadplane-
                            tilthvec|quadplane-tilttri|quadplane-
                            tilttrivec|quadplane-tri|scrimmage-plane
                        ArduSub: gazebo-bluerov2|vectored|vectored_6dof
                        Rover: airsim-rover|balancebot|calibration|gazebo-
                            rover|rover|rover-skid|sailboat|sailboat-motor
                        ArduCopter: +|IrisRos|X|airsim-
                            copter|bfx|calibration|coaxcopter|cwx|djix|dodeca-
                            hexa|gazebo-iris|heli|heli-compound|heli-
                            dual|hexa|hexa-cwx|hexa-dji|octa|octa-cwx|octa-
                            dji|octa-quad|octa-quad-cwx|quad|scrimmage-
                            copter|singlecopter|tri|y6
  -C, --sim_vehicle_sh_compatible
                        be compatible with the way sim_vehicle.sh works; make
                        this the first option
  -H, --hil             start HIL

  Build options:
    -N, --no-rebuild    don't rebuild before starting ardupilot
    -D, --debug         build with debugging
    -c, --clean         do a make clean before building
    -j JOBS, --jobs=JOBS
                        number of processors to use during build (default for
                        waf : number of processor, for make : 1)
    -b BUILD_TARGET, --build-target=BUILD_TARGET
                        override SITL build target
    -s BUILD_SYSTEM, --build-system=BUILD_SYSTEM
                        build system to use
    --enable-math-check-indexes
                        enable checking of math indexes
    --rebuild-on-failure
                        if build fails, do not clean and rebuild
    --waf-configure-arg=WAF_CONFIGURE_ARGS
                        extra arguments to pass to waf in configure step
    --waf-build-arg=WAF_BUILD_ARGS
                        extra arguments to pass to waf in its build step

  Simulation options:
    -I INSTANCE, --instance=INSTANCE
                        instance of simulator
    -n COUNT, --count=COUNT
                        vehicle count; if this is specified, -I is used as a
                        base-value
    -i INSTANCES, --instances=INSTANCES
                        a space delimited list of instances to spawn; if
                        specified, overrides -I and -n.
    -V, --valgrind      enable valgrind for memory access checking (slow!)
    --callgrind         enable valgrind for performance analysis (slow!!)
    -T, --tracker       start an antenna tracker instance
    -A SITL_INSTANCE_ARGS, --sitl-instance-args=SITL_INSTANCE_ARGS
                        pass arguments to SITL instance
    -G, --gdb           use gdb for debugging ardupilot
    -g, --gdb-stopped   use gdb for debugging ardupilot (no auto-start)
    --lldb              use lldb for debugging ardupilot
    --lldb-stopped      use ldb for debugging ardupilot (no auto-start)
    -d DELAY_START, --delay-start=DELAY_START
                        delay start of mavproxy by this number of seconds
    -B BREAKPOINT, --breakpoint=BREAKPOINT
                        add a breakpoint at given location in debugger
    -M, --mavlink-gimbal
                        enable MAVLink gimbal
    -L LOCATION, --location=LOCATION
                        use start location from Tools/autotest/locations.txt
    -l CUSTOM_LOCATION, --custom-location=CUSTOM_LOCATION
                        set custom start location (lat,lon,alt,heading)
    -S SPEEDUP, --speedup=SPEEDUP
                        set simulation speedup (1 for wall clock time)
    -t TRACKER_LOCATION, --tracker-location=TRACKER_LOCATION
                        set antenna tracker start location
    -w, --wipe-eeprom   wipe EEPROM and reload parameters
    -m MAVPROXY_ARGS, --mavproxy-args=MAVPROXY_ARGS
                        additional arguments to pass to mavproxy.py
    --strace            strace the ArduPilot binary
    --model=MODEL       Override simulation model to use
    --use-dir=USE_DIR   Store SITL state and output in named directory
    --no-mavproxy       Don't launch MAVProxy
    --fresh-params      Generate and use local parameter help XML
    --mcast             Use multicasting at default 239.255.145.50:14550
    --osd               Enable SITL OSD
    --tonealarm         Enable SITL ToneAlarm
    --rgbled            Enable SITL RGBLed
    --add-param-file=ADD_PARAM_FILE
                        Add a parameters file to use
    --no-extra-ports    Disable setup of UDP 14550 and 14551 output
    -Z SWARM, --swarm=SWARM
                        Specify path of swarminit.txt for shifting spawn
                        location
    --flash-storage     enable use of flash storage emulation
    --disable-ekf2      disable EKF2 in build
    --disable-ekf3      disable EKF3 in build

  Compatibility MAVProxy options (consider using --mavproxy-args instead):
    --out=OUT           create an additional mavlink output
    --map               load map module on startup
    --console           load console module on startup
    --aircraft=AIRCRAFT
                        store state and logs in named directory
    --moddebug=MODDEBUG
                        mavproxy module debug
    --no-rcin           disable mavproxy rcin

eeprom.bin in the starting directory contains the parameters for your
simulated vehicle. Always start from the same directory. It is recommended
that you start in the main vehicle directory for the vehicle you are
simulating, for example, start in the ArduPlane directory to simulate
ArduPlane
