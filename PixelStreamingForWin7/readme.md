UE5.0.3 使用PixcelStreaming实现像素流流送到浏览器时，在WIN7系统上，UE端启动不了，提示最小要求的系统是win8。



工程开启Plugin: PixelStreaming， HardwareEncoders后，将Plugins目录中的两个文件夹拷到工程所在目录的Plugins目录中。重新生成解决方案，编译解决方案。



工程设置中的平台-Windows下，Targeted RHI 选择Vulkan相关的，不要使用DX相关的