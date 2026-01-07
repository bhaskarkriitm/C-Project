# C-Project
IIT Guwahati C++ Projects
#include <cppcms/application.h>
#include <cppcms/applications_pool.h>
#include <cppcms/service.h>
#include "controllers.h"

int main(int argc,char** argv) {
    try {
        cppcms::service srv(argc,argv);
        srv.applications_pool().mount(
            cppcms::applications_factory<EduConnectApp>()
        );
        srv.run();
    } catch(std::exception const &e) {
        std::cerr << e.what() << std::endl;
    }
    return 0;
}
CREATE TABLE IF NOT EXISTS users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    email TEXT UNIQUE,
    password TEXT
);

CREATE TABLE IF NOT EXISTS courses (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT,
    description TEXT,
    author TEXT
);
#include "models.h"
#include <sqlite3.h>
#include <stdexcept>

static sqlite3* db;

void init_db() {
    if (sqlite3_open("edudb.sqlite", &db))
        throw std::runtime_error("Can't open DB");
}

<!DOCTYPE html>
<html>
<head><title>EduConnect</title></head>
<body>
<h1>EduConnect</h1>
<p>Welcome to your Ed-Tech community.</p>
<a href="/login">Login</a> |
<a href="/courses">Courses</a>
</body>
</html>

#pragma once
void init_db();
