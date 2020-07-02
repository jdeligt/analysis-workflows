To interact with slurm, cromwell requires a backend provider to be defined. I've defined this in the application.conf file. This works and submits a job to slurm. 

However, the runtime attributes are specified in this file as well, i.e cpus, memory, walltime. I want to be able to customize these for individual jobs within a workflow. 
CWL passes these as parameters in the ResoureRequirements section. I can't figure out how to get cromwell to pick the runtime attributes from the cwl ResourceRequirements section. 

Removing the definition in the conf file doesn't work. If I try to refer to any parmeter, cpuMin for example, specified in a ResourceRequirements section it fails with, "Variable cpuMin does not reference any declaration in the task"
From which I'm assuming that cromwell translates the cwl to wdl and is failing somehow to translate the ResourceRequirements section. Wdl will apparently tak the runtime requirements out of the task-level code, so I don't see why it wouldn't take them out of the similar level code from cwl. 

In the cwl I have :
requirements:
    - class: ResourceRequirement
      ramMin: 6000
      tmpdirMin: 25000
      cpuMin: 8
    - class: DockerRequirement
      dockerPull: mgibio/dna-alignment:1.0.0
 
In the cromwell documentation it suggests that cpuMin defaults to cpu if only on of cpuMin and cpuMax is provided, to in the application.conf I've referenced both cpuMin and cpu, neither of which are available. I'm referring to them first in line 55 of the application.conf - it's in the docker sumbit section, which only runs when a command with a docker specified is called. 

The practical upshot of this is that I can submit to slurm, but only with a single set of runtime attributes. 

