# Benchmarks are optional
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/src/fs_benchmark.cpp")
    add_executable(fs_benchmark
        src/benchmark_main.cpp
        src/fs_benchmark.cpp
        src/cache_benchmark.cpp
        src/storage_benchmark.cpp
    )

    target_include_directories(fs_benchmark
        PRIVATE
            ${CMAKE_CURRENT_SOURCE_DIR}/include
    )

    target_link_libraries(fs_benchmark
        PRIVATE
            fs
            cache
            storage
            common
            benchmark
    )

    # Install benchmark executable
    install(TARGETS fs_benchmark
        RUNTIME DESTINATION bin
    )
endif() 