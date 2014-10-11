---
layout: post
title: 修改 CMake VS2010 输出目录
category: cmake
tags: [cmake]
---


CMake创建的project exe文件的输出目录中是包含 $CMAKE_RUNTIME_OUTPUT_DIRECTORY/$BUILD_TYPE/，$BUILD_TYPE(Release/Debug)查看CMake的源码，下面就是写入OutDir的代码(cmVisualStudio10TargetGenerator.cpp)

      
       ...
       this->WritePlatformConfigTag("OutDir", config->c_str(), 3);
      *this->BuildFileStream << outDir
                             << "</OutDir>\n";
       ...
       


加入以下代码

    　//
      const char* defines = this->GeneratorTarget->GetProperty("COMPILE_DEFINITIONS");
      if ( defines )
          if ( strstr( defines, "__SKIP_BUIlD_TYPE_OUT_DIR__") )
              remove_build_type(outDir);
      //
      this->WritePlatformConfigTag("OutDir", config->c_str(), 3);
      *this->BuildFileStream << outDir
                             << "</OutDir>\n";
      ...


      // ../xxx/Release/  => /xxx/    
      void remove_build_type(std::string& dir) {
      
          std::string tmp = dir;
          int pos = tmp.length();
          pos--;
          int remove_count = 0;
          while( pos > 0  )
          {
              if ( tmp[pos] == '\\' )
                 remove_count++;
              if ( remove_count >= 2 )
                 break;
              pos--;
          }
          dir = tmp.substr(0,pos+1);      
     }    


CMakeLists.txt加入

     
    add_definitions( -D__SKIP_BUIlD_TYPE_OUT_DIR__ )
    




