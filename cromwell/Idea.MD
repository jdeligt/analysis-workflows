## CWL config
Other people have a config like this:
        Int cpu = 1
        Int memory_mb = 2048
        String queue = "campus-haswell.q"
        String pename = "openmp"
        String memtype = "mem_type"
        
        Int? cpuMin
        Int? cpuMax
        Int? memoryMin
        Int? memoryMax
        String? outDirMin
        String? outDirMax
        String? tmpDirMin
        String? tmpDirMax


There might be some usefull tidbits here:
https://github.com/bcbio/bcbio-nextgen/issues/2697
