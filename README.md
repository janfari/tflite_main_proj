# tflite_main_proj
tflite toy zephyr project for debugging

# Setup
1. Clone this repo into a workspace directory ie "tf-ws"
2. `west init`
 - change the path in .west/config if necessary
        ```
        [manifest]
        path = tflite_main_proj
        file = west.yml

        [zephyr]
        base = zephyr
        ```
3. `west update` This should download `tflite_sub_proj` as well the nrf, modules, and zephyr folders
4. The app in tflite_main_proj/app can be built using the nrf vs code extension or via the comand line. The board we are configured for is the `nrf5340dk_nrf5340_cpuapp`
