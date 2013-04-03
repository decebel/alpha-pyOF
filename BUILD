
** building boost on windows **

- download boost from boost.org
- build bjam first by running the bootstrap.bat script
- run bjam such as below: (by default this will only build the dynamic version of the libraries)
>> bjam
- for building static variants do the following:
>> bjam --toolset=msvc link=static threading=multi runtime-link=static


** building mongo client **
- download scons 
- modify SConstruct script. Find line elif "win32" == os.sys.platform:. In this section add
env.Append( EXTRACPPPATH=[ "C:/work/externals/boost_1_51_0" ] )
>> scons -j4 --dd --use-system-boost mongoclient.lib
Also I had to disable existence check of boost binary libraries which looked like
  for b in boostLibs:
        l = "boost_" + b
        if not conf.CheckLib([ l + boostCompiler + "-mt" + boostVersion,
                               l + boostCompiler + boostVersion ], language='C++' ):
            Exit(1)