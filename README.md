# parse_openvr_using_clang

To be able to write tools for openvr and openvr's multiple versions
it would be nice to generate API bindings by parsing the C++ headers
as well as to combine the openvr json files. 

This will then be used to:
* way writing trampoline functions to intercept calls and insert behaviours
* insert call tracing
* connect to plugins 
* generate all sorts of tools as well as to refactor https://github.com/spayne/openvr_strings 


* parse openvr headers using libclang to generate utility files

===================================================================
* attempt one: use some rando's ideas
* result: no build instructions

** references: https://shaharmike.com/cpp/libclang/

** build dependencies
sudo apt-get install libclang-10-dev 
sudo apt-get install clang 
dpkg -L libclang-10-dev

===================================================================
* attempt two: build using official sources
* build fails
references: https://clang.llvm.org/docs/Tooling.html
references: https://clang.llvm.org/docs/LibASTMatchersTutorial.html
sudo apt-get install python3 libssl-dev
how to build useful source to source translationtooling based on clang's libtooling

fixes: 
* build/ needs to be inside of my clang-llvm/llvm-project/ directory
* started build at 14:06. ninja failed with 'build.ninja' still dirty after 100 tries
* clean and try again at 14:23.  15:09 still building... [3711/5491]

* 15:19 failed to link.  possibly ran out of memory?  
[3752/5491] Linking CXX executable bin/clang-12
FAILED: bin/clang-12 
collect2: fatal error: ld terminated with signal 9 [Killed]

* try running top and ninja with only one job (-j1)
   * 15:20: ld is taking 12.9g of virtual memory (42%)
worked!
   * 15:24 [43/1731]
   * 15:44 [207/1731] - continue using regular ninja

* 1600 linking bin/clangd failed. so try ninja -j1 again

todo:
consider adding more swap



===================================================================
* attempt three: try apt-get clang-tools
dpkg -L clang-tools
* result some random tools

===================================================================
* attempt four: try building clang using main instructions, then go back to the tutorial

re



#consider just using existing ninja and cmake
#or work through step 0
#instead of bootstra.py, use:
python3 configure.py --bootstrap 

#use this clone instead
git clone https://github.com/Kitware/CMake cmake

#dont checkout next
./bootstrap works



setting up clangtoolsing
