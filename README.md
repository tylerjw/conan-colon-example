# Conan - Colcon Example

This is a basic example of consuming a conan library package in a ROS 2 package.

## Create the hello conan package

```shell
conan create hello_conan_lib
```

## Build the ROS 2 package

Install the conan dependencies of the ros2 package(s)
```shell
conan install ros2 --output-folder=build --build=missing
```

Build colcon package hello_ros
```shell
colcon build --base-paths ros2 --cmake-args -DCMAKE_TOOLCHAIN_FILE=$PWD/build/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release
```

Run the executable
```shell
./build/hello_ros/hello_ros
```

## Project Structure

- `hello_conan_lib` : library that can be packaged with conan
- `ros2` : base of ros2 packages, note the `--base-paths ros` arg passed to `colcon`
- `ros2/conanfile.txt` : conan file describing the dependencies needed by ROS 2 packages to build

## Tooling

We need to pass the `CMAKE_TOOLCHAIN_FILE` argument to colcon to enable it to find the conan packages durring the build.
