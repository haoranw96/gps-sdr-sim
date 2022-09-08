# GPS-SDR-SIM

### compile gps-sdr-sim
```
gcc gpssim.c -lm -O3 -o gps-sdr-sim -DUSER_MOTION_SIZE=4000
```

### install hackrf_transfer
```
sudo port install gr-osmosdr +full
sudo port install gr-fosphor
sudo port install Gqrx
hackrf_info
osmocom_fft -F
# hackrf_transfer -t test.bin -f 432000000 -s 2000000
```

### prepare gpssim.bin file for transfer
```
# gpssim_30s.bin
./gps-sdr-sim -b 8 -e brdc1570.22n -l 33.7752438,-84.3895558,342.0 -d 30
hackrf_transfer -t gpssim.bin -f 1575420000 -s 2600000 -a 1 -x 0

# 120 seconds
./gps-sdr-sim -b 8 -e brdc1570.22n -l 33.7752438,-84.3895558,342.0 -d 120  # 342 meter
./gps-sdr-sim -b 8 -e brdc1570.22n -l 33.7752438,-84.3895558,300.0 -d 120  # 300 meter
hackrf_transfer -t gpssim.bin -f 1575420000 -s 2600000 -a 1 -x 0

# 240 seconds
./gps-sdr-sim -b 8 -e brdc1570.22n -l 33.7752438,-84.3895558,330.0 -d 240
hackrf_transfer -t gpssim.bin -f 1575420000 -s 5200000 -a 1 -x 0
```

###### no idea 
```
python3 sub-sample.py
```