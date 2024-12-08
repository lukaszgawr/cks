# CIS Benchmarks
CIS = Center for Internet Security
  ```
  sh ./Assessor-CLI.sh -i -rd /var/www/html/ -nts -rp index 
 --------------------------------------------------------------------------------------
   ,o88888o.    8888    d888888o.          ,o88888o.           8.    8888888888888888 
  8888    `88.  8888  .`8888:' `88.       8888    `88.        .88.         8888       
,88888      `8. 8888  8.`8888.   Y8     ,88888      `8.      .8888.        8888       
888888          8888  `8.`8888.         888888              .`88888.       8888       
888888          8888   `8.`8888.   888  888888             .8.`88888.      8888       
888888          8888    `8.`8888.  888  888888            .8`8.`88888.     8888       
888888          8888     `8.`8888.      888888           .8' `8.`88888.    8888       
`88888      .8' 8888 8b   `8.`8888.     `88888      .8' .8'   `8.`88888.   8888       
  8888    ,88'  8888 `8b.  ;8.`8888       8888    ,88' .888888888.`88888.  8888       
   `888888P'    8888  `Y8888P ,88P'        `888888P'  .8'       `8.`88888. 8888       
--------------------------------------------------------------------------------------
         Welcome to CIS-CAT Pro Assessor; built on 09/24/2024 21:10 PM
--------------------------------------------------------------------------------------
  This is the Center for Internet Security Configuration Assessment Tool, v4.46.0
          At any time during the selection process, enter 'q!' to exit.
--------------------------------------------------------------------------------------

Verifying application

Configured report output directory to '/var/www/html/'
Configured report naming prefix to 'index'
Attempting to load the default sessions.properties, bundled with the application.
Started Assessment 1/1

Loading Benchmarks/Data-Stream Collections

Available Benchmarks/Data-Stream Collections:
 1. CIS Controls Assessment Module - Implementation Group 1 for Windows 10 v1.0.3
 2. CIS Controls Assessment Module - Implementation Group 1 for Windows Server v1.0.0
 3. CIS Google Chrome Benchmark v3.0.0
 4. CIS Microsoft Windows 10 Enterprise Benchmark v3.0.0
 5. CIS Microsoft Windows 10 Stand-alone Benchmark v3.0.0
 6. CIS Microsoft Windows 11 Enterprise Benchmark v3.0.0
 7. CIS Ubuntu Linux 20.04 LTS Benchmark v2.0.1
 > Select Content # (max 7): 7 


Selected 'CIS Ubuntu Linux 20.04 LTS Benchmark'

Assessment File CIS_Ubuntu_Linux_20.04_LTS_Benchmark_v2.0.1-xccdf.xml has a valid Signature.
Profiles:
1. Level 1 - Server
2. Level 2 - Server
3. Level 1 - Workstation
4. Level 2 - Workstation
 > Select Profile # (max 4): 1

Selected Profile 'Level 1 - Server'
  ```
  
Benchmarks/Data-Stream Collections: e.g.: CIS Ubuntu Linux 20.04 LTS Benchmark v2.0.1

Profile: e.g. Level 1 - Server