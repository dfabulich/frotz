# Makefile for Unix Frotz
# GNU make is required

SDL_PKGS ?= libpng libjpeg sdl2 SDL2_mixer freetype2 zlib

SOURCES = sf_fonts.c sf_msg_en.c sf_resource.c sf_util.c \
	sf_deffont.c sf_ftype.c sf_osfdlg.c sf_sig.c sf_video.c \
	sf_font3.c sf_images.c sf_sound.c generic.c

HEADERS = sf_frotz.h

OBJECTS = $(SOURCES:.c=.o)

DEPS = $(SOURCES:.c=.d)

TARGET = frotz_sdl.a

ARFLAGS = rc

.PHONY: clean
.DELETE_ON_ERROR:

$(TARGET): $(OBJECTS)
	$(AR) $(ARFLAGS) $@ $?
	$(RANLIB) $@
	@echo "** Done with SDL interface."

clean:
	-rm -f $(TARGET) $(OBJECTS) $(DEPS)

%.o: override CFLAGS += $(shell $(PKGCONF) $(SDL_PKGS) --cflags) $(SDL_CFLAGS)

%.o: %.c
	$(CC) $(CFLAGS) -fPIC -fpic -o $@ -c $<
