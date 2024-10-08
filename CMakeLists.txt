cmake_minimum_required(VERSION 3.8)
project(executors_exercises_pkg)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(std_msgs REQUIRED)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # uncomment the line when a copyright and license is not present in all source files
  #set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # uncomment the line when this package is not in a git repo
  #set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

add_executable(executor_example_1_node src/executor_example_1.cpp)
ament_target_dependencies(executor_example_1_node rclcpp)

add_executable(executor_example_2_node src/executor_example_2.cpp)
ament_target_dependencies(executor_example_2_node rclcpp nav_msgs)

add_executable(executor_example_3_node src/executor_example_3.cpp)
ament_target_dependencies(executor_example_3_node rclcpp nav_msgs)

add_executable(executor_example_3_static_node src/executor_example_3_static.cpp)
ament_target_dependencies(executor_example_3_static_node rclcpp nav_msgs)

add_executable(executor_example_4_node src/executor_example_4.cpp)
ament_target_dependencies(executor_example_4_node rclcpp nav_msgs)

add_executable(executor_example_4_singlethreaded_node src/executor_example_4_singlethreaded.cpp)
ament_target_dependencies(executor_example_4_singlethreaded_node rclcpp nav_msgs)

add_executable(executor_example_5_node src/executor_example_5.cpp)
ament_target_dependencies(executor_example_5_node rclcpp)

add_executable(executor_example_5_reentrant_node src/executor_example_5_reentrant.cpp)
ament_target_dependencies(executor_example_5_reentrant_node rclcpp)

add_executable(executor_example_5_mutuallyexclusive_node src/executor_example_5_mutuallyexclusive.cpp)
ament_target_dependencies(executor_example_5_mutuallyexclusive_node rclcpp)

add_executable(executor_example_5_mutuallyexclusive_multiple_node src/executor_example_5_mutuallyexclusive_multiple.cpp)
ament_target_dependencies(executor_example_5_mutuallyexclusive_multiple_node rclcpp)

add_executable(box_bot_manager_node src/box_bot_manager.cpp)
ament_target_dependencies(box_bot_manager_node rclcpp nav_msgs geometry_msgs)

add_executable(wait_for_box_bots_arrive_node src/wait_for_box_bots_arrive.cpp)
ament_target_dependencies(wait_for_box_bots_arrive_node rclcpp std_msgs)

add_executable(wait_for_box_bots_arrive_static_node src/wait_for_box_bots_arrive_static.cpp)
ament_target_dependencies(wait_for_box_bots_arrive_static_node rclcpp std_msgs)

add_executable(wait_for_box_bots_arrive_condition_node src/wait_for_box_bots_arrive_condition.cpp)
ament_target_dependencies(wait_for_box_bots_arrive_condition_node rclcpp std_msgs)

install(TARGETS 
		executor_example_1_node
		executor_example_2_node
		executor_example_3_node
		executor_example_3_static_node
		executor_example_4_node
		executor_example_4_singlethreaded_node
		executor_example_5_node
		executor_example_5_reentrant_node
		executor_example_5_mutuallyexclusive_node
		executor_example_5_mutuallyexclusive_multiple_node
		box_bot_manager_node
		wait_for_box_bots_arrive_node
		wait_for_box_bots_arrive_static_node
		wait_for_box_bots_arrive_condition_node
		DESTINATION lib/${PROJECT_NAME}
)

install(DIRECTORY
		launch
		DESTINATION share/${PROJECT_NAME}
)

ament_package()
