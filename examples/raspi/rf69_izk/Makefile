# Makefile
# Sample for RH_RF69HCW (client and server) on Raspberry Pi
# Caution: requires bcm2835 library to be already installed
# http://www.airspayce.com/mikem/bcm2835/

CC            = g++
CFLAGS        = -DRASPBERRY_PI -DBCM2835_NO_DELAY_COMPATIBILITY -D__BASEFILE__=\"$*\" -DRFM69_HW
LIBS          = -lbcm2835 -lrt
RADIOHEADBASE = ../../..
INCLUDE       = -I$(RADIOHEADBASE)

all: rf69_client rf69_server

RasPi.o: $(RADIOHEADBASE)/RHutil_izk/RasPi.cpp
				$(CC) $(CFLAGS) -c $(RADIOHEADBASE)/RHutil_izk/RasPi.cpp $(INCLUDE)

rf69_client.o: rf69_client.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

rf69_server.o: rf69_server.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RH_RF69.o: $(RADIOHEADBASE)/RH_RF69.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHHardwareSPI.o: $(RADIOHEADBASE)/RHHardwareSPI.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHSPIDriver.o: $(RADIOHEADBASE)/RHSPIDriver.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHGenericDriver.o: $(RADIOHEADBASE)/RHGenericDriver.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHGenericSPI.o: $(RADIOHEADBASE)/RHGenericSPI.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

rf69_client: rf69_client.o RH_RF69.o RasPi.o RHHardwareSPI.o RHGenericDriver.o RHGenericSPI.o RHSPIDriver.o
				$(CC) $^ $(LIBS) -o rf22b_client

rf69_server: rf69_server.o RH_RF69.o RasPi.o RHHardwareSPI.o RHGenericDriver.o RHGenericSPI.o RHSPIDriver.o
				$(CC) $^ $(LIBS) -o rf22b_server
clean:
				rm -rf *.o rf69_client rf69_server
