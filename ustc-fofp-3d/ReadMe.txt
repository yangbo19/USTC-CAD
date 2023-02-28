
Run Platform: Linux system.
Implement tool: C language.

The executable file name is  "3dfp".

Run the executable file：./3dfp benchmark (eg.: ./3dfp n100).


The 2D and 3D program code are put in the 2D and 3D folder respectively.

fl.prm file is the configuration file, setting parameter values:

sparearea   whitespace fraction

aspect_ratio   aspect ratio


start_tempe    start temperature in Simulated Annealing(SA)
end_tempe      end temperature in SA
iterations     inner loops in SA
cooling_ratio  cooling proportion

layers         number of ties

out_wire       1-ouput wire connections; 0-not output wire connections     

ant_time       loop times in Ant System (AS) algorithm

//the balance factors of objective function in SA
deltac_wgt     area 
deltnt_wgt     wire-length
deltvia_wgt    TSV

//the balance factors of objective function in AS
deltac_wt      area
deltnt_wt      wire-length
deltvia_wt     TSV

In main.c file, we also set some parameters used in AS

ant     population numbers
alpha and beta are parameters used in Roulette wheel selection of AS

NewPopGen() function is to generate new solutions in AS，containing the Roulette wheel selection and probability layer assignment strategy.


AS to generate globally optimal solutions in the first phase, which are then improved by the SA-based searching algorithm in the second phase.

SimulatedAnnealing() function is the SA-based searching algorithm.

OutputCellsForMultiTiers（）is the output function, ouput the information of the best floorplan searched by the algorithm (for 3D).
Output() (for 2D）.

Parameters Setting Value：

For 3D Floorplaner

start_tempe    100000
end_tempe      100
iterations     120
cooling_ratio  0.9

layers         4

ant_time       10

n100, n200 benchmark：
  
deltac_wgt     0.994
deltnt_wgt     0.004
deltvia_wgt    0.002

deltac_wt      0.6
deltnt_wt      0.2
deltvia_wt     0.2

n300 benchmark：
  
deltac_wgt     0.992
deltnt_wgt     0.004
deltvia_wgt    0.004

deltac_wt      0.6
deltnt_wt      0.2
deltvia_wt     0.2

For 2D Floorplaner

start_tempe    200000
end_tempe      100
iterations     150
cooling_ratio  0.9

layers         4

ant_time       10

n10,n50,n100,n200 benchmark：
  
deltac_wgt     0.998
deltnt_wgt     0.002
deltvia_wgt    0

deltac_wt      0.75
deltnt_wt      0.25
deltvia_wt     0

ami33, ami49 benchmark：
  
deltac_wgt     0.998
deltnt_wgt     0.002
deltvia_wgt    0

deltac_wt      0.60
deltnt_wt      0.4
deltvia_wt     0

The results are stored in file <test_case_name>.txt.
After execute the program, you will obtain file <test_case_name>_layer.plt in the <test_case_name>-fp directory.

The file contains the blocks position of each layer and the wire connections (if out_wire equals to 1).

If you want to draw the floorplan, you can execute instruction: gnuplot n100_layer.plt.


