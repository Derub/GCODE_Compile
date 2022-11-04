# GCODE_Compile
MATLAB G-Code compiler starting from GCODE_array notation, adapted on Osellami FLM platforms


SINTAX: 
[CompiledFileName]=GCODE_Compile(name,n,mode,setup,x_GCODE,y_GCODE,z_GCODE,v_GCODE, shutter_GCODE,wait_GCODE,motion_GCODE,radius_GODE, *incipit*)
or [CompiledFileName]=GCODE_Compile(name,n,mode,setup,GCODE_array, *incipit*)

GCODE_array: a matrix with either 8 or 9 columns. Each column represent one of the possible vectors described below. the order is the following
GCODE_array = [x_GCODE,y_GCODE,z_GCODE,v_GCODE, shutter_GCODE,wait_GCODE,motion_GCODE,radius_GODE, *angle_GCODE*]

  x_GCODE,y_GCODE,z_GCODE: series of 3D coordinates of points array that
  define the variuos points connected by LINEAR movements. 
  REMARK:z_GCODE can be empty and the structure will be written only along xy
  plane

  v_GCODE: speed of the movement

  shutter_GCODE: flag for the shutter. If 1, the linear point is reached
  with open shutter, if 0 with closed shutter

  wait_CODE: Wait is a pause before the movement. can be 'auto', 'nowait' or an array of positive values. in case of
  auto,  for every command the
  compiler insert a wait (0.1 in case of
  shutter closure, 0.01 ms otherwise). If nowait, no wait is added between
  commands or shutters. If an array, each linear is evaluated depending
  on the value of wait_gcode. The wait time is a delay before the motion
  and after the laser switch (i.e. the order tir shutter-wait-motion)

  motion_GCODE: can be "linear" or an array of 1,0,-1 indicating with 0 a LINEAR movement, with 1
  and -1 a XY cirular movement in clockwise or counterclockwise direction

  radius_GCODE: radius for circular movement

  n: refractive index of the media 

  mode:'incremental' or 'absolute'

  setup:'Line1', 'AntGalvo' , 'Bee' ,'Capable' or 'Ant'

  incipit: (optional) inital comment for the description of the code
