########################################################################
## Feature registration
########################################################################
cmake_dependent_option(ENABLE_BLOCKS_PACKET "Enable Pothos Blocks.Packet component" ON "ENABLE_BLOCKS;JSON_HPP_INCLUDE_DIR" OFF)
add_feature_info("  Packet" ENABLE_BLOCKS_PACKET "Packet to/from stream converter blocks")
if (NOT ENABLE_BLOCKS_PACKET)
    return()
endif()

########################################################################
# Packet blocks module
########################################################################
include_directories(${JSON_HPP_INCLUDE_DIR})
POTHOS_MODULE_UTIL(
    TARGET PacketBlocks
    SOURCES
        PacketToStream.cpp
        StreamToPacket.cpp
        TestPacketBlocks.cpp
    DESTINATION blocks
    ENABLE_DOCS
)
