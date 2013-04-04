
** building boost on windows **

- download boost from boost.org
- build bjam first by running the bootstrap.bat script
- run bjam such as below: (by default this will only build the dynamic version of the libraries)
>> bjam
- for building static variants do the following:
>> bjam --toolset=msvc link=static threading=multi runtime-link=static


** building mongo client **
- download scons 
- download mongo 2.0.9
- - In mongodb source, comment file: util/text.cpp (comment line around 94)
>>//throw boost::system::system_error(
>> // ::GetLastError(), boost::system::system_category);

- In the SConstruct file change the /MT switch for release build to /MD since openframeworks project is set to /MD in release build
>> scons --release mongoclient

To build the debug version, use:
>> scons --debug mongoclient




** below notes are experiments with the latest versions. Not proven stable yet
- modify SConstruct script. Find line elif "win32" == os.sys.platform:. In this section add
env.Append( EXTRACPPPATH=[ "C:/work/externals/boost_1_51_0" ] )
>> scons -j4 --dd --use-system-boost mongoclient.lib
Also I had to disable existence check of boost binary libraries which looked like
  for b in boostLibs:
        l = "boost_" + b
        if not conf.CheckLib([ l + boostCompiler + "-mt" + boostVersion,
                               l + boostCompiler + boostVersion ], language='C++' ):
            Exit(1)