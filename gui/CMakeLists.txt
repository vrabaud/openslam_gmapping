find_package(Qt4 )
include(${QT_USE_FILE})

qt4_wrap_cpp(MOC_QGRAPHPAINTER qgraphpainter.h)
qt4_wrap_cpp(MOC_QPARTICLEVIEWER qparticleviewer.h)

include_directories(../include/gmapping ../ ../include/gmapping/log/ ../)

#add_executable(gfs_nogui gfs_nogui.cpp)

add_executable(gfs_simplegui gfs_simplegui.cpp qgraphpainter.cpp qparticleviewer.cpp
  gsp_thread ../configfile/configfile.cpp ${MOC_QGRAPHPAINTER} ${MOC_QPARTICLEVIEWER})
target_link_libraries(gfs_simplegui gridfastslam gmapping_log sensor_odometry
  ${QT_LIBRARIES} pthread)

#add_executable(gfs2img gfs2img.cpp gridfastslam)

#-include ../global.mk

#OBJS= gsp_thread.o qparticleviewer.o qgraphpainter.o qmappainter.o 

#APPS= gfs_nogui gfs_simplegui gfs2img
#LDFLAGS+=  $(QT_LIB) $(KDE_LIB) -lgridfastslam -lscanmatcher -llog -lsensor_range -lsensor_odometry -lsensor_base -lconfigfile -lutils -lpthread

#ifeq ($(CARMENSUPPORT),1)
#LDFLAGS+= -lcarmenwrapper 
#endif

#CPPFLAGS+= -I../sensor $(QT_INCLUDE) $(KDE_INCLUDE) -I$(CARMEN_HOME)/include


#-include ../build_tools/Makefile.generic-shared-object



