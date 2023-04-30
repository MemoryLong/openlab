#!/bin/bash
# Copyright (C) 2016 The CyanogenMod Project
# Copyright (C) 2017 The LineageOS Project
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# yum方式安装
yum -y install postgresql-server.x86_64
# 初始化
/usr/bin/postgresql-setup initdb

# 启动postgresql
systemctl start postgresql
# 检查postgresql状态
systemctl status postgresql
# 配置开机自启动
systemctl enable postgresql

# q切换用户
su postgres
# 进入postgresql
psql
# 创建用户sonar
create user sonar with password '123456';
# 创建sonarqube数据库
create database sonarqube owner sonar;
# 退出
\q
exit

vi /var/lib/pgsql/data/postgresql.conf
新增listen_addresses = ‘*’远程连接
vi /var/lib/pgsql/data/pg_hba.conf
新增 host all all 0.0.0.0/0 trust 访问规则

# 在/var/lib/pgsql/data/postgresql.conf新增listen_addresses = ‘*’，监听全部IP
sed -i '$a listen_addresses = ‘*’' /var/lib/pgsql/data/postgresql.conf    

# 在/var/lib/pgsql/data/postgresql.conf新增listen_addresses = ‘*’，监听全部IP
sed -i '$a host all all 0.0.0.0/0 trust' /var/lib/pgsql/data/pg_hba.conf    
