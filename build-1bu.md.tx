--- First time setup ---

0. Install packages: 

sudo apt install build-essential

sudo apt-get install ccache

sudo apt-get install libssl-dev


1. Clone Vantom kernel:

git clone https://github.com/vantoman/kernel_xiaomi_sm6150.git -b courbet-12.1


2. Clone AnyKernel: 

git clone https://github.com/osm0sis/AnyKernel3.git


3. Clone Playground Clang:

git clone https://gitlab.com/PixelOS-Devices/playgroundtc.git


--- Building --- 


1. Set your export path: 

export PATH="/PATH/TO/CLANG/bin/:$PATH" 

for example: 

export PATH="/home/redline-soee/kernel/playgroundtc/bin/:$PATH"


2. Move to kernel directory: 

cd kernel_xiaomi_sm6150


2.5 (Optional) Build for high panel dimensions (MIUI vendor roms): 

a) Revert this commit: 

git revert e349d4d92a79ba33039610867a882a9276125669

b) When the kernel is compiled use git reset --hard HEAD~ to get back the commit


3. Write the configuration to .config: 

make O=out ARCH=arm64 sweet_defconfig 


4. Compile the kernel:

time make -j$(nproc --all) O=out ARCH=arm64 CC="ccache clang" AR=llvm-ar NM=llvm-nm OBJCOPY=llvm-objcopy OBJDUMP=llvm-objdump STRIP=llvm-strip LD=ld.lld CROSS_COMPILE=aarch64-linux-gnu- CROSS_COMPILE_ARM32=arm-linux-gnueabi- LLVM=1 LLVM_IAS=1


5. Go to the out folder: 

out\arch\arm64\boot


6. Get Image.gz and dtbo.img files and replace them with existing ones in an AnyKernel zip (you can use a zip from a previous kernel release)


7. Remove the out folder: 

rm -rf out
