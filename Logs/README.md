# Writing Logs
Logging is an essential part of software development for debugging, monitoring, and maintaining applications. Here are some best practices and professional ways to write log messages in C++ projects:

1.  **Use a Logging Library:**
    
    *   Instead of reinventing the wheel, consider using a logging library that fits your needs. Popular C++ logging libraries include:
        *   [spdlog](https://github.com/gabime/spdlog)
        *   [glog](https://github.com/google/glog)
        *   [log4cpp](http://log4cpp.sourceforge.net/)
        *   [Boost.Log](https://www.boost.org/doc/libs/1_77_0/libs/log/doc/html/index.html)
2.  **Log Levels:**
    
    *   Use different log levels (e.g., DEBUG, INFO, WARNING, ERROR, FATAL) to categorize messages based on their severity.
    *   Adjust log levels dynamically to control the verbosity of the logs.
3.  **Log Formatting:**
    
    *   Include relevant information in log messages, such as timestamps, log levels, file names, line numbers, and function names.
    *   Use a consistent log message format across your application for better readability.
4.  **Avoid Excessive Logging:**
    
    *   Be mindful of the amount of logging in your code. Excessive logging can impact performance and make it challenging to find important information in logs.
5.  **Contextual Information:**
    
    *   Include context-specific information in log messages. For example, include the current user, transaction ID, or any other relevant details that can aid in debugging.
6.  **Logging Configuration:**
    
    *   Allow configuration of logging settings externally, so you can adjust logging behavior without modifying code (e.g., change log levels, output destinations).
7.  **Thread Safety:**
    
    *   If your application is multithreaded, ensure that your logging library or logging code is thread-safe to avoid race conditions and data corruption.
8.  **Error Handling:**
    
    *   Log appropriate error messages when exceptions or errors occur. Include enough information to understand the cause of the error.
9.  **Log Rotation and Retention:**
    
    *   Implement log rotation and retention policies to manage log file sizes and prevent them from consuming too much disk space.
10.  **Use Descriptive Log Messages:**
    
    *   Write log messages that provide meaningful information about what is happening. Avoid overly cryptic or unclear messages.
11.  **Unit Testing:**
    
    *   Consider unit testing your logging code to ensure that log messages are generated as expected.
12.  **Logging in Release Builds:**
    
    *   Be cautious about logging sensitive information in release builds. Use conditional compilation or configure your logging library accordingly to exclude certain messages in release mode.
13.  **Documentation:**
    
    *   Document your logging conventions and guidelines for developers working on the project. Make sure everyone is aware of how logging is intended to be used.

## Example
```
#include <iostream>
#include <chrono>
#include <iomanip>
#include <thread>

// Get current timestamp as a string
std::string currentTimestamp() {
    auto now = std::chrono::system_clock::now();
    auto now_c = std::chrono::system_clock::to_time_t(now);

    std::stringstream ss;
    ss << std::put_time(std::localtime(&now_c), "%F %T");
    return ss.str();
}

// Define macro for log location
#define LOG_LOCATION "[File: " << __FILE__ << ", Line: " << __LINE__ << ", Function: " << __FUNCTION__ << "]"

// Define macro for thread ID
#define LOG_THREAD_ID "[Thread: " << std::this_thread::get_id() << "]"

// Define macro for log levels
#define LOG_DEBUG std::cout << "[" << currentTimestamp() << "] [DEBUG] " << LOG_LOCATION << " " << LOG_THREAD_ID << " "
#define LOG_INFO std::cout << "[" << currentTimestamp() << "] [INFO] " << LOG_LOCATION << " " << LOG_THREAD_ID << " "
#define LOG_WARNING std::cerr << "[" << currentTimestamp() << "] [WARNING] " << LOG_LOCATION << " " << LOG_THREAD_ID << " "
#define LOG_ERROR std::cerr << "[" << currentTimestamp() << "] [ERROR] " << LOG_LOCATION << " " << LOG_THREAD_ID << " "

// Example usage
int main() {
    LOG_INFO << "This is an informational message." << std::endl;

    // Simulate an error condition
    LOG_ERROR << "An error occurred." << std::endl;

    return 0;
}

```