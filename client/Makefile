CXXFLAGS=-Wall -O3 -I../common -I.
OBJECTS=udp-flaschen-taschen.o

MAGICK_CXXFLAGS=`GraphicsMagick++-config --cppflags --cxxflags`
MAGICK_LDFLAGS=`GraphicsMagick++-config --ldflags --libs`

FFMPEG_LDFLAGS=`pkg-config --cflags --libs  libavcodec libavformat libswscale libavutil`

all : simple-example simple-animation mandelbrot

simple-animation: simple-animation.cc $(OBJECTS)

simple-example: simple-example.cc $(OBJECTS)

mandelbrot: mandelbrot.cc $(OBJECTS)

send-image : send-image.cc $(OBJECTS)
	$(CXX) $(CXXFLAGS) $(MAGICK_CXXFLAGS) -o $@ $^ $(MAGICK_LDFLAGS)

send-video: send-video.cc $(OBJECTS)
	$(CXX) $(CXXFLAGS) -o $@ $^ $(FFMPEG_LDFLAGS)

% : %.cc
	$(CXX) $(CXXFLAGS) -o $@ $^

clean:
	rm -f send-image send-video simple-example simple-animation $(OBJECTS)
