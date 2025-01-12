# Adafruit Bus IO Library
# https://github.com/adafruit/Adafruit_BusIO
# MIT License

idf_build_get_property(__hack_component_targets __COMPONENT_TARGETS)

if("arduino" IN_LIST BUILD_COMPONENTS OR __hack_component_targets MATCHES "__idf_arduino")
    list(APPEND ADAFRUIT_BUSIO_REQUIRES
        arduino
    )
elseif("framework-arduinoespressif32" IN_LIST BUILD_COMPONENTS OR __hack_component_targets MATCHES "___idf_framework-arduinoespressif32")
    list(APPEND ADAFRUIT_BUSIO_REQUIRES
        framework-arduinoespressif32
    )
elseif("espressif__arduino-esp32" IN_LIST BUILD_COMPONENTS OR __hack_component_targets MATCHES "___idf_espressif__arduino-esp32")
    list(APPEND ADAFRUIT_BUSIO_REQUIRES
        espressif__arduino-esp32
    )
endif()

idf_component_register(SRCS "Adafruit_I2CDevice.cpp" "Adafruit_BusIO_Register.cpp" "Adafruit_SPIDevice.cpp" 
                       INCLUDE_DIRS "."
                       PRIV_REQUIRES ${ADAFRUIT_BUSIO_REQUIRES})

project(Adafruit_BusIO)
