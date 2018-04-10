# xmr-stak -- Ubuntu 17.10 / AMD Ryzen 7 1700

Personalized README for CPU mining with [fireice-uk/xmr-stak](https://github.com/fireice-uk/xmr-stak) on my workstation.

## Usage

```sh
./bin/xmr-stak --noAMD --noNVIDIA --currency monero7 \
  -o stratum+tcp://cryptonightv7.eu.nicehash.com:3363 \
  -u 3Qsz9ZbmxYojJcGxwm2KqG631yA38wt7gY -p x \
  --use-nicehash -i 8037
```

## Building from source

```
sudo apt install libmicrohttpd-dev libssl-dev cmake build-essential libhwloc-dev
git clone https://github.com/fireice-uk/xmr-stak.git
mkdir xmr-stak/build
cd xmr-stak/build
cmake ..
make install
```
