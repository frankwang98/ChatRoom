# chatproject
a chatproject C++ from lanqiaowang

## install
sudo apt-get install build-essential libmysqlclient-dev libmysqlcppconn-dev

## run
make

## Q&A
### bind: Address already in use
sudo lsof -i :<端口号> # 查找占用端口的进程
sudo kill -9 <PID> # 关闭占用端口的进程
或等待一段时间后再尝试启动应用程序，可能会使端口空闲