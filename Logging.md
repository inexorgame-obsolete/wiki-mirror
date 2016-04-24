Branches | Issues | Main developers
--- | --- | --- 
easylogging |  [#290](/inexor-game/code/pull/290) | [@a-teammate](/a-teammate), [@aschaeffer](/aschaeffer)

## Motivation

Logging is an important requirement for software nowadays.

* Log levels
 * Debug
 * Info
 * Warn
 * Error
 * Critical
* Log targets (= Sinks)
 * Inexor Ingame Console
 * Stdout / Stderr
 * Daily Logfile
 * Rotating Logfile
 * MSVC
 * Syslog
* Log format
 * Date / Time
 * Logger name
 * Log level
 * Message

## Default loggers in Inexor

* global
* chat
* gameplay
* edit
* server
* frag_involved
* frag_not_involved

## Cubescript commands

* loglevel <logger_name> <log_level>
 * Example: /loglevel "global" "warning"
* logformat <logger_name> <pattern>
 * Example: /logformat "global" "%H:%M:%S [%n] [%l] %v"

## How to use the loggers

### Creating Sinks

    std::vector<spdlog::sink_ptr> sinks;
    sinks.push_back(std::make_shared<spdlog::sinks::stdout_sink_st>());
    sinks.push_back(std::make_shared<inexor::util::InexorConsoleSink>());
    sinks.push_back(std::make_shared<inexor::util::InexorCutAnsiCodesSink>(std::make_shared<spdlog::sinks::daily_file_sink_st>("inexor", "log", 23, 59)));

### Creating Loggers 

    auto global = std::make_shared<spdlog::logger>("global", begin(sinks), end(sinks));
    auto chat = std::make_shared<spdlog::logger>("chat", begin(sinks), end(sinks));
    auto gameplay = std::make_shared<spdlog::logger>("gameplay", begin(sinks), end(sinks));
    auto edit = std::make_shared<spdlog::logger>("edit", begin(sinks), end(sinks));
    auto server = std::make_shared<spdlog::logger>("server", begin(sinks), end(sinks));
    auto frag_involved = std::make_shared<spdlog::logger>("frag_involved", begin(sinks), end(sinks));
    auto frag_not_involved = std::make_shared<spdlog::logger>("frag_not_involved", begin(sinks), end(sinks));

### Register Loggers

    spdlog::register_logger(global);
    spdlog::register_logger(chat);
    spdlog::register_logger(gameplay);
    spdlog::register_logger(edit);
    spdlog::register_logger(server);
    spdlog::register_logger(frag_involved);
    spdlog::register_logger(frag_not_involved);

### Using Loggers

    spdlog::get("global")->debug() << "Debug message " << some_var << " " << some_other_var;
    spdlog::get("global")->info() << "Info message " << some_var << " " << some_other_var;
    spdlog::get("global")->warn() << "Warning message " << some_var << " " << some_other_var;
    spdlog::get("edit")->error() << "Error message " << some_var << " " << some_other_var;

    auto global_logger = spdlog::get("global");
    global_logger->info() << "Message";

### SPD Logger Documentation

1. https://github.com/gabime/spdlog/wiki/1.-QuickStart
2. https://github.com/gabime/spdlog/wiki/2.-Creating-loggersformatting
3. https://github.com/gabime/spdlog/wiki/3.-Custom-
4. https://github.com/gabime/spdlog/wiki/4.-Sinks
5. https://github.com/gabime/spdlog/wiki/5.-Logger-registry
