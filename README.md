# FWData

FWData is all CMSSW data product dictionary and suppoting sources. The libraries built can be used in reading RECO and AOD ROOT files for the CMS Experiment

## Building and running with spack

- Clone spack and cmssw-spack and run build
```
git clone https://github.com/spack/spack.git
git clone -b fwdata https://github.com/gartung/cmssw-spack.git
source spack/share/setup-env.sh
spack compiler add --scope site
spack repo add --scope site $PWD/cmssw-spack
spack install fwdata
```

- Setup runtime environment with spack
```
source spack/share/setup-env.sh
spack load -r fwdata
export LD_LIBRARY_PATH=$LIBRARY_PATH:$LD_LIBRARY_PATH
root.exe step3.root
```
