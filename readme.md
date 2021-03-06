# One-axis stage to move a filter

This is a parametrizable open-source hardware (OSH) stage to move an optical filter. 
The dimensions of the filter and the stage are parametrizable in order to change the dimensions of the stage, the filter and any other components (stepper motor, belt tensioner, aluminum profiles,..)
The printable pieces are described using [FreeCAD](http://freecadweb.org/) Python scripts.
It can be compared with the OpenSCAD version: https://github.com/felipe-m/oscad_filter_stage

1. [License](#license)
2. [Description](#description)
3. [Assembly](#assembly)
4. [Main parameters](#main_parameters)
    1. [Filter Holder Parameters](#filter_holder_param)
    2. [Belt Tensioner](#belt_tensioner_param)
5.  [Project organization](#directory)
6.  [Printable Parts](#printed_parts)
    1. [Parts with step by step tutorial](#tutorial_step)
    2. [The rest of the parts](#no_tutorial)
7.  [Print settings](#print_set)

    
**The pictures of this readme.md are reduced in size to make the document more readable** larger pictures can be found in the img folder (see [Project organization](#directory))

---
## License <a name="license"></a>


Hardware License: CERN 1.2 (https://ohwr.org/cernohl)

Software License: [LGPL 3.0](./License.md)

Documentation License: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/)

![ES000004](imgs/small/OSHW_mark_ES000004.png )

This project has been certified as [open source hardware](https://certification.oshwa.org/es000004.html) by the [Open Source Hardware Association](https://www.oshwa.org/). 


## Description <a name="description"></a>

The components of the stage are:
* Filter holder
* Timming belt
* Belt tensioner
* Stepper motor with pulley
* Motor holder
* Linear guide
* Some nuts and bolts

![Filter Stage Names](imgs/small/filter_stage/filter_stage_name.jpg )

---

## Assembly <a name="assembly"></a>

### Filter holder

The filter holder holds an optical filter and it is attached to a linear guide. 

![Filter Holder Names](imgs/small/filter_holder/filter_holder_names.jpg )


It has various holes to be able to fit in different linear guides

![Filter Holder Exploded](imgs/small/filter_holder/filter_holder_exploded_name.jpg )


### Belt tensioner

The belt tensioner is composed by 2 printable parts, and idler pulley:
* Tensioner holder
* Idler tensioner
* Idler pulley
* Leadscrew with nut

![Belt tensioner front](imgs/small/belt_tensioner/tensioner_names.jpg )

Back view of the belt tensioner:

![Belt tensioner back](imgs/small/belt_tensioner/tensioner_names_back.jpg )

Exploded view of the belt tensioner:

![Belt tensioner exploded](imgs/small/belt_tensioner/tensioner_set_exploded_names.jpg )

By turning the leadscrew, the idler pulley will retract or extend, tightening or loosening the belt. 

Retracted belt tensioner:

![Belt tensioner retracted](imgs/small/belt_tensioner/idler_tensioner_side.jpg )

Extended belt tensioner:

![Belt tensioner extended](imgs/small/belt_tensioner/idler_tensioner_side_extend.jpg )

The idler pulley can be made out of a bearing, a bolt, a nut and some washers. 
For example, if using a DIN 912 bolt, it can be built this way:

![Idler pulley bearing](imgs/belt_tensioner/idler_tensioner_pulley_name.png )

---

## Main Parameters <a name="main_parameters"></a>
Following, the main parameters are explained.
There are some other parameters that can be seen in the Python code.

---

### Filter Holder Parameters <a name="filter_holder_param"></a>


![Filter holder parameters](imgs/filter_holder/filter_holder_params.png)

Example of 2 filter holders having different parameters:

![2 Filter holder size](imgs/small/filter_holder/filter_holder_2sizes.jpg)

---

### Belt tensioner Parameters <a name="belt_tensioner_param"></a>


Idler tensioner size depending on the idler pulley:

![Idler tensioner size depending on the idler pulley](imgs/small/belt_tensioner/idler_tensioner_idler_pulley_top.jpg)

---

The tensioner stroke can be modified:

![tensioner stroke](imgs/small/belt_tensioner/idler_tensioner_stroke_draw.png)

---

The thickness of the walls can be modified

![tensioner wall thick](imgs/small/belt_tensioner/wall_thick.jpg)

---

The metric size of the leadscrew can be modified:

![Leadscrew size](imgs/small/belt_tensioner/leadscrew_metric.jpg)

---

These modifications lead to automatic modifications on the tensioner holder size:

![Tensioner holder size](imgs/small/belt_tensioner/tensioner_holder_ex_2idlertens.jpg)

---

The belt height is parametrizable, leading to modifications on the tensioner holder:

![Belt height](imgs/small/belt_tensioner/belt_height.png)

---

![Belt height](imgs/small/belt_tensioner/tensioner_set_3belt_h.jpg)


---

The base width, ie. the aluminum profile width, is parametrizable:

![Base width](imgs/small/belt_tensioner/tensioner_holder_ex_3profiles_side.jpg)



---

## Project organization <a name="directory"></a>
```
 +--- scr: Source files in Python
    +--- comps: functions in Python for FreeCAD, https://github.com/felipe-m/fcad-comps
 +--- scr_cq: Source files in Python using CadQuery   
 +--- freecad: Saved FreeCAD designs
 +--- stl: Parts exported to STL
 +--- imgs: Images of the 4 parts in png format
    +--- small: reduced size images
    +--- tens_hold_steps: images for the step by step explanation for the tensioer holder
    +--- idler_tens_steps: images for the step by step explanation for the idler tensioner
    +--- belt_tensioner: belt tensioner images
    +--- filter_holder: filter holder images
    +--- filter_stage: filter stage images
```

 comps: are python functions and classes to make the shapes easier. Check https://github.com/felipe-m/fcad-comps

---


 
## Step by step explanations <a name="printed_parts"></a>:

### Step by step explanations <a name="tutorial_step"></a>:

1. [tensioner_holder.md](./tensioner_holder.md) Detailed explanation for the tensioner holder. It also includes information on how to execute the Python scripts. 
![Tensioner Holder](imgs/small/tens_holder.png )
1. [idler_tensioner.md](./idler_tensioner.md) Detailed explanation for the idler tensioner
![Idler Tensioner](imgs/small/idler_tensioner.png )


You can compare the same pieces designed using OpenSCAD: https://github.com/felipe-m/oscad_filter_stage

---

### Designs with no step by step explanations <a name="no_tutorial"></a>:
1. The [tensioner_set.py](src/tensioner_set.py) module has no detailed explanation, but the code is explained based on the previous. This code combines the parts of the tensioner set and uses Python classes and methods.
![Tensioner Set](imgs/small/tensioner_set.png )
1. [filter_holder_clss.py](src/filter_holder_clss.py) Filter holder, similar to the one made with OpenSCAD (https://github.com/felipe-m/oscad_filter_stage)
![Filter Holder](imgs/small/filter_holder.png )
1. [filter_stage.py](src/filter_stage.py) In the same design includes the filter holder, the belt tensioner and the motor holder, and also some other non-printable models, such as the stepper motor, aluminum profile, linear guide, belt and pulleys
![Filter Stage](imgs/small/filter_stage_1.png )
1. CadQuery designs have no step-by-step explanations, but there are comments in the code:
 + [cq_idler_tensioner.py](src_cq/cq_idler_tensioner.py)
 + [cq_tensioner_holder.py](src_cq/cq_tensioner_holder.py)
 + [cq_nemamotor_bracket.py](src_cq/cq_nemamotor_bracket.py)
 + [cq_filter_holder.py](src_cq/cq_filter_holder.py)
 
## Print settings <a name="print_set"></a>:

There is no need to have supports as long as the parts are printed with the following orientation:

![Print orientation](imgs/small/filter_stage/filter_stage_printable_parts_2.jpg)






