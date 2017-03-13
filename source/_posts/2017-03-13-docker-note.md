---
title: Docker 學習筆記
date: 2017-03-13 22:53:23
categories:
- Learn
- Docker
tags: docker
---
最近因為新開發一個案子，測試使用 Docker 來進行佈屬程式
中間也遇到了些問題，所以希望可以把查詢到的資料先做個筆記，以備不時之需
<!--more-->

# 基本觀念
## Docker Image
1. 包含了完整的基礎 root 檔案系統(以Linux來說)
2. 作為系統樣版，供 Container 運行

## Docker Container
1. Image 對比 Container，就像是程式中的`Class`與`Instance`
2. Container 實際上就像是系統中的一個 Process，因此不同於 VM，
   在 Container 的環境中，必須要有一個 main process 正在執行，
   而當這個 main process 結束後，這個 Container 也會隨之關閉
3. 同第2點，許多人可能把 Container 當作 VM 的概念，
   於是在建立 Container 後，執行一個背景執行程式(Service)，但是 Container 很快就會關閉了，
   這是因為 Container 並沒有一個 main process 正在執行，
   所以使用 Container 時，必須使用前景運行的方式來執行所想要的服務

# Docker for Windows 與 Windows Container
1. Container 技術最早出現在 Linux 上，因此 Windows 想要使用就只能透過 Linux VM
2. 最早要在 Windows 上使用 Docker，需要安裝 Docker Toolbox
   主要是透過 Virtual Box 執行 Linux VM 來操作 Docker
   但是既然 Windows 有 Hyper-V，可以運用 Hyper-V 的 VM，效能上應該比 Virtual Box 來的好
3. 於是在 Microsoft 與 Docker 的配合下 Docker for Windows 出現了(應該是吧!)
   使用 Hyper-V 建立的 Apline Linux + Busybox，以及原生的管理介面
4. 但是畢竟還是只能執行 Linux 的 Container，也就是基礎上還是使用 Linux 的系統，
   於是 Microsoft 也打造自己的 Container 技術， 並且擁抱 Docker 的管理指令，
   這樣就不用額外學習新的指令就可以使用 Windows Container，
   當然在 Windows Container 中就可以執行在 Windows 的程式(ex. IIS、MQSQL...)

# 指令筆記
* 清除沒有使用的 volumes `
docker volume rm $(docker volume ls -q --filter dangling=true)`
* 清除無效的 images `docker rmi $(docker images -f "dangling=true" -q)`

# 參考資料
[(GitBook)Docker — 从入门到实践](https://www.gitbook.com/book/yeasy/docker_practice/details)
[(GitBook)Docker學習筆記](https://www.gitbook.com/book/peihsinsu/docker-note-book/details)
[Docker CLI Reference](https://docs.docker.com/engine/reference/commandline/cli/)
