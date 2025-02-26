## [Intel OpenVINO toolkit](https://software.intel.com/en-us/openvino-toolkit)

### Requirements

* Intel Core with 6th generation and higher or Intel Xeon CPUs.

### Preparation

* Download [OpenVINO toolkit 2018R5](https://software.intel.com/en-us/openvino-toolkit) .tgz installer (offline or online) for Ubuntu platforms.
* Put downloaded file into ```cvat/components/openvino```.
* Accept EULA in the `cvat/components/eula.cfg` file.

### Build docker image
```bash
# From project root directory
docker-compose -f docker-compose.yml -f components/openvino/docker-compose.openvino.yml build
```

### Run docker container
```bash
# From project root directory
docker-compose -f docker-compose.yml -f components/openvino/docker-compose.openvino.yml up -d
```

You should be able to login and see the web interface for CVAT now, complete with the new "Model Manager" button.

### OpenVINO Models

Clone the [Open Model Zoo](https://github.com/opencv/open_model_zoo). `$ git clone https://github.com/opencv/open_model_zoo.git`

Install the appropriate libraries. Currently that command would be `$ pip install -r open_model_zoo/tools/downloader/requirements.in`

Download the models using `downloader.py` file in `open_model_zoo/tools/downloader/`. 
The `--name` command can be used to specify specific models. 
The `--print_all` command can print all the available models. 
Specific models that are already integrated into Cvat can be found [here](https://github.com/opencv/cvat/tree/develop/utils/open_model_zoo).

From the web user interface in CVAT, upload the models using the model manager.
You'll need to include the xml and bin file from the model downloader.
You'll need to include the python and JSON files from scratch or by using the ones in the CVAT libary. 
See [here](https://github.com/opencv/cvat/tree/develop/cvat/apps/auto_annotation) for instructions for creating custom 
python and JSON files.
