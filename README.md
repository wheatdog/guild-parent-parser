```
$ guild run argparse-parent-test
You are about to run argparse-parent-test
  sub-float: 2.2
  sub-int: 2
Continue? (Y/n) n

$ guild check
guild_version:             0.7.0.rc9
guild_install_location:    /home/wheatdog/miniconda3/envs/guild-test/lib/python3.7/site-packages/guild
guild_home:                /home/wheatdog/miniconda3/envs/guild-test/.guild
guild_resource_cache:      /home/wheatdog/miniconda3/envs/guild-test/.guild/cache/resources
installed_plugins:         cpu, disk, exec_script, gpu, keras, memory, perf, python_script, queue, skopt
python_version:            3.7.4 (default, Aug 13 2019, 20:35:49) [GCC 7.3.0]
python_exe:                /home/wheatdog/miniconda3/envs/guild-test/bin/python
platform:                  Linux 5.6.6-arch1-1 x86_64
psutil_version:            5.6.3
tensorboard_version:       1.15.0
cuda_version:              not installed
nvidia_smi_version:        not installed
latest_guild_version:      unknown (error)

$ python main.py --help
usage: main.py [-h] [--main-int MAIN_INT] [--main-float MAIN_FLOAT]
               [--sub-int SUB_INT] [--sub-float SUB_FLOAT]

optional arguments:
  -h, --help            show this help message and exit
  --main-int MAIN_INT
  --main-float MAIN_FLOAT
  --sub-int SUB_INT
  --sub-float SUB_FLOAT

$ LOG_LEVEL=10 python -m guild.plugins.import_argparse_flags_main main.py '' output
DEBUG: [import_flags_main] loading module from 'main.py'
DEBUG: [import_flags_main] handling add_argument: ('--main-int',) {'type': <class 'int'>, 'default': 1}
DEBUG: [import_flags_main] added flag {'default': 1}
DEBUG: [import_flags_main] handling add_argument: ('--main-float',) {'type': <class 'float'>, 'default': 1.2}
DEBUG: [import_flags_main] added flag {'default': 1.2}
DEBUG: [import_flags_main] handling add_argument: ('-h', '--help') {'action': 'help', 'default': '==SUPPRESS==', 'help': 'show this help message and exit'}
DEBUG: [import_flags_main] skipping _HelpAction(option_strings=['-h', '--help'], dest='help', nargs=0, const=None, default='==SUPPRESS==', type=None, choices=None, help='show this help message and exit', metavar=None) - not an action type
DEBUG: [import_flags_main] handling add_argument: ('--sub-int',) {'type': <class 'int'>, 'default': 2}
DEBUG: [import_flags_main] added flag {'default': 2}
DEBUG: [import_flags_main] handling add_argument: ('--sub-float',) {'type': <class 'float'>, 'default': 2.2}
DEBUG: [import_flags_main] added flag {'default': 2.2}
DEBUG: [import_flags_main] writing flags to output: {'sub-int': {'default': 2}, 'sub-float': {'default': 2.2}}
usage: main.py [-h] [--main-int MAIN_INT] [--main-float MAIN_FLOAT]
               [--sub-int SUB_INT] [--sub-float SUB_FLOAT]

optional arguments:
  -h, --help            show this help message and exit
  --main-int MAIN_INT
  --main-float MAIN_FLOAT
  --sub-int SUB_INT
  --sub-float SUB_FLOAT

$ cat output
{"sub-int": {"default": 2}, "sub-float": {"default": 2.2}}
```
