CC = clang
CXX = clang++


PHONELIBS = ../phonelibs

WARN_FLAGS = -Werror=implicit-function-declaration \
             -Werror=incompatible-pointer-types \
             -Werror=int-conversion \
             -Werror=return-type \
             -Werror=format-extra-args

CFLAGS = -std=gnu11 -fPIC -O2 $(WARN_FLAGS)
CXXFLAGS = -std=c++11 -fPIC -O2 $(WARN_FLAGS)

NANOVG_FLAGS = -I$(PHONELIBS)/nanovg

OPENGL_LIBS = -lGLESv3

FRAMEBUFFER_LIBS = -lutils -lgui -lEGL

COMMON_OBJS = ../selfdrive/common/glutil.o \
       ../selfdrive/common/framebuffer.o \
       $(PHONELIBS)/nanovg/nanovg.o \
       ../selfdrive/common/spinner.o \
       opensans_semibold.o \
       img_spinner_track.o \
       img_spinner_comma.o


DEPS := $(OPENPILOT_OBJS_shane_car_tuning-074_default:.o=.d) $(OPENPILOT_OBJS_shane_car_tuning-075_default:.o=.d) $(OPENPILOT_OBJS_shane_df-tf_default:.o=.d) $(OPENPILOT_OBJS_shane_e2e_long-075_default:.o=.d) $(OPENPILOT_OBJS_shane_master_default:.o=.d) $(OPENPILOT_OBJS_shane_phantom-07_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-07_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-071_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-074_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-075-staging_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-devel_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-release_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_devel_staging_default:.o=.d) $(OPENPILOT_OBJS_shane_stock_devel_default:.o=.d) $(OPENPILOT_OBJS_shane_traffic_lights-074_default:.o=.d) $(OPENPILOT_OBJS_shane_car_tuning-074_cn:.o=.d) $(OPENPILOT_OBJS_shane_car_tuning-075_cn:.o=.d) $(OPENPILOT_OBJS_shane_df-tf_cn:.o=.d) $(OPENPILOT_OBJS_shane_e2e_long-075_cn:.o=.d) $(OPENPILOT_OBJS_shane_master_cn:.o=.d) $(OPENPILOT_OBJS_shane_phantom-07_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-07_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-071_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-074_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-075-staging_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-devel_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions-release_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_additions_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_devel_staging_cn:.o=.d) $(OPENPILOT_OBJS_shane_stock_devel_cn:.o=.d) $(OPENPILOT_OBJS_shane_traffic_lights-074_cn:.o=.d) 
.PHONY: all
all: installers/installer_shane_stock_additions_default installers/installer_shane_stock_additions_cn

OPENPILOT_OBJS_shane_stock_additions_default = installer_shane_stock_additions_default.o continue_openpilot.o $(COMMON_OBJS)

installer_shane_stock_additions_default.o: installer.c
	@echo "[ CC ] $@"
	$(CC) $(CFLAGS) -MMD -I.. -I../selfdrive -DBRAND=openpilot -DBRANCH=stock_additions -DGITURL='https:\/\/github.com\/ShaneSmiskol\/openpilot' -c -o '$@' '$<'

installers/installer_shane_stock_additions_default: $(OPENPILOT_OBJS_shane_stock_additions_default)
	@echo "[ LINK ] $@"
	$(CXX) -fPIC -o '$@' $^ -s $(FRAMEBUFFER_LIBS) -L/system/vendor/lib64 $(OPENGL_LIBS) -lm -llog



OPENPILOT_OBJS_shane_stock_additions_cn = installer_shane_stock_additions_cn.o continue_openpilot.o $(COMMON_OBJS)

installer_shane_stock_additions_cn.o: installer.c
	@echo "[ CC ] $@"
	$(CC) $(CFLAGS) -MMD -I.. -I../selfdrive -DBRAND=openpilot -DBRANCH=stock_additions -DGITURL='https:\/\/github.com.cnpmjs.org\/ShaneSmiskol\/openpilot' -c -o '$@' '$<'

installers/installer_shane_stock_additions_cn: $(OPENPILOT_OBJS_shane_stock_additions_cn)
	@echo "[ LINK ] $@"
	$(CXX) -fPIC -o '$@' $^ -s $(FRAMEBUFFER_LIBS) -L/system/vendor/lib64 $(OPENGL_LIBS) -lm -llog



../selfdrive/common/framebuffer.o: ../selfdrive/common/framebuffer.cc
	@echo "[ CXX ] $@"
	$(CXX) $(CXXFLAGS) -MMD \
           -I$(PHONELIBS)/android_frameworks_native/include \
           -I$(PHONELIBS)/android_system_core/include \
           -I$(PHONELIBS)/android_hardware_libhardware/include \
           -c -o '$@' '$<'

../selfdrive/common/spinner.o: ../selfdrive/common/spinner.c
	@echo "[ CXX ] $@"
	$(CXX) $(CXXFLAGS) -MMD \
          -I$(PHONELIBS)/android_frameworks_native/include \
          -I$(PHONELIBS)/android_system_core/include \
          -I$(PHONELIBS)/android_hardware_libhardware/include \
          $(NANOVG_FLAGS) \
          -c -o '$@' '$<'

opensans_semibold.o: ../selfdrive/assets/fonts/opensans_semibold.ttf
	@echo "[ bin2o ] $@"
	cd '$(dir $<)' && ld -r -b binary '$(notdir $<)' -o '$(abspath $@)'

img_spinner_track.o: ../selfdrive/assets/img_spinner_track.png
	@echo "[ bin2o ] $@"
	cd '$(dir $<)' && ld -r -b binary '$(notdir $<)' -o '$(abspath $@)'

img_spinner_comma.o: ../selfdrive/assets/img_spinner_comma.png
	@echo "[ bin2o ] $@"
	cd '$(dir $<)' && ld -r -b binary '$(notdir $<)' -o '$(abspath $@)'



%.o: %.c
	@echo "[ CC ] $@"
	$(CC) $(CFLAGS) -MMD \
          -I.. -I../selfdrive \
          -c -o '$@' '$<'

%.o: %.sh
	@echo "[ bin2o ] $@"
	cd '$(dir $<)' && ld -r -b binary '$(notdir $<)' -o '$(abspath $@)'

.PHONY: clean
clean:
	rm -f installers/installer_*
	rm -f *.o *.d

-include $(DEPS)