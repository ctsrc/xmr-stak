# xmr-stak -- Ubuntu 17.10 / AMD Ryzen 7 1700

Personalized README for CPU mining with [fireice-uk/xmr-stak](https://github.com/fireice-uk/xmr-stak) on my workstation.

This README is current as of commit [e10e8e6](https://github.com/ctsrc/xmr-stak/commit/e10e8e67492cf3118af8b7d7609937e85e572305) to the xmr-stak master branch.

## Usage

```sh
cd ~/src/github.com/fireice-uk/xmr-stak/build/
./bin/xmr-stak --noAMD --noNVIDIA --currency monero7 \
  -o stratum+tcp://cryptonightv7.eu.nicehash.com:3363 \
  -u 3Qsz9ZbmxYojJcGxwm2KqG631yA38wt7gY -p x -r CPU \
  --use-nicehash -i 8037
```

## Build from source

```bash
sudo apt install libmicrohttpd-dev libssl-dev cmake build-essential libhwloc-dev
mkdir -p ~/src/bin/github.com/fireice-uk
cd !$
git clone https://github.com/fireice-uk/xmr-stak.git
mkdir xmr-stak/build
cd xmr-stak/build
cmake ..
make install
```

## Enable large page support and increase ulimit -l

See https://github.com/xmrig/xmrig/issues/32 and
https://github.com/fireice-uk/xmr-stak/blob/master/doc/FAQ.md#error-memory-alloc-failed-mmap-failed

```bash
echo vm.nr_hugepages=128 | sudo dd oflag=append conv=notrunc of=/etc/sysctl.conf
sudo sysctl -p

sudo dd oflag=append conv=notrunc of=/etc/security/limits.conf <<EOF
* soft memlock 262144
* hard memlock 262144
EOF
```

Log out and then log back in for the ulimit take effect.
