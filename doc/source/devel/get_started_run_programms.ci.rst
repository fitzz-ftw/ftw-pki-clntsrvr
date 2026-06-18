Running the programm Successfully and Errors
==============================================

.. SECTION - Setup
>>> test_data_pre= "test_clientserver_data"

>>> from fitzzftw.devtools.testinfra import TestHomeEnvironment
>>> from pathlib import Path
>>> env = TestHomeEnvironment(Path("doc/source/devel/testhome"))
>>> env.setup(True)
>>> env.clean_home()

.. !SECTION - Setup
.. SECTION - Prepare

>>> from pathlib import Path

>>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")

>> def stub_getpass(prompt:str)->str:
...     print(prompt)
...     return "strenggeheim"

>>> cmd_line="--conf-file tim_notebook.toml  "
>>> cmd_line += " -k tim-note"
>>> cmd_line += " -dns tim.member.example.org"
>>> cmd_line += " tim@example.org"

>>> import shlex
>>> sys_argv= shlex.split(cmd_line) 
>>> sys_argv #doctest: +NORMALIZE_WHITESPACE
['--conf-file', 'tim_notebook.toml', 
 '-k', 'tim-note', 
 '-dns', 'tim.member.example.org', 
 'tim@example.org']



.. !SECTION - Prepare
.. SECTION - Start programm function

>>> from ftwpki.client_server.programms import prog_client_server_csr
>>> prog_client_server_csr(sys_argv, prog="ftwpkiclient")
0

>>> cmd_line="--conf-file tim_notebook.toml  "

>>> cmd_line += " -k tim-note "
>>> cmd_line += " www-admin@example.org"

>>> sys_argv= shlex.split(cmd_line) 

>>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")
>>> prog_client_server_csr(sys_argv) #doctest: +ELLIPSIS
Error: At least an ip address or a hostname has to be given
1

>>> cmd_line="--conf-file tim_notebook.toml  "
>>> cmd_line += " -k tim-note"
>>> cmd_line += " --private-dir privat"
>>> cmd_line += " -dns www.secure.example.org"
>>> sys_argv= shlex.split(cmd_line)

>>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")


>>> prog_client_server_csr(sys_argv) #doctest: +ELLIPSIS
Error: the following arguments are required: email
1


>>> cmd_line="--conf-file tim_notebook.toml  "
>>> cmd_line += " -k tim-note"
>>> cmd_line += " -dns org"
>>> cmd_line += " www-admin@example.org"

>>> sys_argv= shlex.split(cmd_line)

>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")


>>> prog_client_server_csr(sys_argv) #doctest: +ELLIPSIS
Error: Hostname 'org' is not a FQDN (missing dot).
1

>>> cmd_line="--conf-file tim_notebook.toml  "
>>> cmd_line += " -k tim-note"
>>> cmd_line += " --private-dir privat"
>>> cmd_line += " -dns localhost"
>>> cmd_line += " www-admin@example.org"

>>> sys_argv= shlex.split(cmd_line)
>>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")

>>> prog_client_server_csr(sys_argv)
0

>>> cmd_line="--conf-file tim_notebook.toml  "
>>> cmd_line += " -k tim-note"
>>> cmd_line += " --private-dir privat"
>>> cmd_line += " -dns localhost"
>>> cmd_line += " -ip 127.0.0.1"
>>> cmd_line += " www-admin@example.org"

>>> sys_argv= shlex.split(cmd_line)
>>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")
>>> prog_client_server_csr(sys_argv)
0

>>> cmd_line="--conf-file tim_notebook.toml  "
>>> cmd_line += " -k tim-note"
>>> cmd_line += " --private-dir privat"
>>> cmd_line += " -ip org"
>>> cmd_line += " www-admin@example.org"

>>> sys_argv= shlex.split(cmd_line)
>>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")
>>> prog_client_server_csr(sys_argv) #doctest: +ELLIPSIS
Error: 'org' does not appear to be an IPv4 or IPv6 address
1

>>> cmd_line = " --private-dir privat"
>>> cmd_line += " -k tim-note"
>>> cmd_line += " -ip 192.168.1.1"
>>> cmd_line += " www-admin@example.org"

>>> sys_argv= shlex.split(cmd_line)
>>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")

>>> prog_client_server_csr(sys_argv) #doctest: +ELLIPSIS
Error: the following arguments are required: --conf-file
1

Error: expected str, bytes or os.PathLike object, not NoneType
1

>>> cmd_line="--conf-file tim_notebook.toml  "
>>> cmd_line += " -k tim-note"
>>> cmd_line += " -C DE"
>>> cmd_line += " -CN 'IT-Security Server'"
>>> cmd_line += " --private-dir privat"
>>> cmd_line += " -ip 192.168.1.1"
>>> cmd_line += " www-admin@example.org"

>>> sys_argv= shlex.split(cmd_line)

>>> conf_file = env.copy2cwd(f"{test_data_pre}/leaf_client_notebook_conf.toml", "tim_notebook.toml")
>>> prog_client_server_csr(sys_argv)
0

.. !SECTION - Start programm function

.. SECTION - Teardown

>>> env.clean_home()
>>> env.teardown()

.. !SECTION - Teardown
