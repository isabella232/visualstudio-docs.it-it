---
title: Configurazione di Remote R Service in Linux
description: Come configurare Remote R Service in Ubuntu e nel sottosistema di Windows per Linux.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: b0703d8523066914bad00c8313600a63b8cb0f06
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2021
ms.locfileid: "114680136"
---
# <a name="remote-r-service-for-linux"></a>Remote R Service per Linux

Remote R Service per Linux è attualmente disponibile in un pacchetto come rtvs-daemon. Il daemon è supportato e testato in Ubuntu 16.04, 16.10 LTS desktop, server e nel sottosistema Windows per Linux che esegue Ubuntu. Gran parte di questo articolo include istruzioni per la configurazione di Remote R Service in questi sistemi diversi.

Dopo aver configurato il computer remoto, i passaggi seguenti consentono di connettere R Tools for Visual Studio (RTVS) a tale servizio:

1. Selezionare **R Tools**  >  **Windows**  >  **aree di lavoro** per aprire la finestra Aree **di** lavoro.
1. Selezionare **Aggiungi connessione**.
1. Assegnare un nome alla connessione e specificare l'URL, ad esempio `https://localhost:5444` (sottosistema Windows per Linux) o `https://public-ip:5444` (contenitore di Azure). Al termine, selezionare **Salva**.
1. Selezionare l'icona della connessione o fare doppio clic sull'elemento della connessione.
1. Fornire le credenziali di accesso. Al nome utente deve essere aggiunto il prefisso `<<unix>>\`, come in `<<unix>>\ruser1`, richiesto per tutte le connessioni a computer remoti Linux.
1. Se si usa un certificato autofirmato, potrebbe essere visualizzato un avviso. Il messaggio include istruzioni per risolvere l'avviso.

## <a name="set-up-remote-r-service"></a>Configurare Remote R Service

In questa sezione vengono descritte le opzioni seguenti:

- [Computer Ubuntu fisico](#physical-ubuntu-computer)
- [Macchina virtuale del server Ubuntu o macchina virtuale data science in Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Contenitore Docker locale o remoto (compilazione pulita)](#local-or-remote-docker-container-clean-build)
- [Contenitore in esecuzione in Istanze di Azure Container](#container-running-on-azure-container-instances)

In ogni caso, nel computer remoto deve essere installato uno degli interpreti R seguenti:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R per Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Computer Ubuntu fisico

1. Dopo aver eseguito l'accesso al computer, scaricare il file tarball di rtvs-daemon:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Eseguire lo script di installazione:

    ```bash
    sudo ./rtvs-install
    ```

    Per un'installazione invisibile all'utente, usare `sudo ./rtvs-install -s`.

1. Abilitare e avviare il servizio:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Configurare il certificato SSL (richiesto per la produzione). Per impostazione predefinita, rtvs-daemon usa i file `ssl-cert-snakeoil.pem` e `ssl-cert-snakeoil.pem` generati dal pacchetto `ssl-cert`. Durante l'installazione vengono combinati in `ssl-cert-snakeoil.pfx`. Per scopi di produzione, usare il certificato SSL fornito dall'amministratore. Il certificato SSL può essere configurato specificando un file con estensione *pfx* e una password facoltativa per l'importazione in: */etc/rtvs/rtvsd.config.json*.

1. (Facoltativo) Controllare che il servizio sia in esecuzione:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Se non è disponibile un processo in esecuzione con il nome utente `rtvssvc`. Avviarlo con il comando seguente:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Per ulteriori configurazioni di rtvs-daemon, vedere `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Macchina virtuale del server Ubuntu o macchina virtuale data science in Azure

#### <a name="create-a-vm"></a>Creare una VM

1. Accedere al [portale di Azure](https://portal.azure.com).
1. Passare a Macchine virtuali e quindi selezionare **Aggiungi**.
1. Nell'elenco delle immagini di macchine virtuali disponibili cercare e selezionare una delle voci seguenti:
    - Server Ubuntu: `Ubuntu Server 16.04 LTS`
    - Macchina virtuale data science: `Linux Data Science` (per altri dettagli, vedere [Macchine virtuali di analisi scientifica dei dati](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/))
1. Impostare il modello di distribuzione su `Resource manager` e selezionare **Crea**.
1. Scegliere un nome per la macchina virtuale, specificare nome utente e password (la password è obbligatoria perché non è supportato l'accesso con chiave pubblica SSH).
1. Apportare le altre modifiche eventualmente desiderate alla configurazione della macchina virtuale.
1. Scegliere una dimensione di macchina virtuale, verificare la configurazione e selezionare **Crea**. Dopo aver creato la macchina virtuale, procedere alla sezione successiva.

#### <a name="configure-the-vm"></a>Configurare la macchina virtuale

1. Nella sezione **Rete** della macchina virtuale aggiungere 5444 come porta in ingresso consentita. Per usare una porta diversa, modificare l'impostazione nel file di configurazione del daemon RTVS (*/etc/rtvs/rtvsd.config.json*).
1. (Facoltativo) Impostare un nome DNS. È anche possibile usare l'indirizzo IP.
1. Connettersi alla macchina virtuale con un client SSH, ad esempio PuTTY per WIndows.
1. Seguire le istruzioni sopra riportate per un [computer Ubuntu fisico](#physical-ubuntu-computer).

### <a name="windows-subsystem-for-linux-wsl"></a>Sottosistema di Windows per Linux (WSL)

1. Seguire le istruzioni di installazione del sottosistema Windows per Linux per [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) o [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Avviare Bash in Windows e seguire le istruzioni precedenti per un [computer Ubuntu fisico](#physical-ubuntu-computer) con una eccezione. Nel passaggio 3 avviare il servizio con il comando `rtvsd`, perché il sottosistema Windows per Linux attualmente non supporta le interfacce systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Contenitore Docker locale o remoto (compilazione pulita)

1. Creare un file Docker con il contenuto riportato di seguito, che installa il daemon di Remote R Service e la versione più recente di R. **Nota**: questo script crea un utente denominato "ruser1" con la password "foobar", che è possibile modificare nel modo desiderato nelle ultime due istruzioni `RUN`.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Compilare ed eseguire il file Docker:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Per connettersi al contenitore da RTVS, usare il percorso `https://localhost:5444`, il nome utente `<<unix>>\ruser1` e la password `foobar`. Se il contenitore è in esecuzione in un computer remoto, usare invece il percorso `https://remote-host-name:5444`. La porta può essere modificata aggiornando */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Contenitore in esecuzione in Istanze di Azure Container

1. Seguire le istruzioni in [Contenitore Docker locale o remoto (compilazione pulita)](#local-or-remote-docker-container-clean-build) per creare l'immagine.
1. Eseguire il push del contenitore nell'hub Docker o in Azure Container Repository.
1. Avviare l'interfaccia della riga di comando di Azure ed eseguire l'accesso con il comando `az login`.
1. Usare il comando `az container create` per creare il contenitore, usando `--command-line "rtvsd"` se il contenitore non è stato configurato per l'esecuzione di `rtvsd` come servizio `systemd`. Nel comando seguente è previsto che l'immagine si trovi nell'hub Docker. È anche possibile usare Azure Container Repository aggiungendo gli argomenti per le credenziali del repository alla riga di comando.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Usare il comando `az container list` per controllare lo stato. Cercare `provisioningState`: `Succeeded`.
1. Se il provisioning ha esito positivo, è ora possibile connettersi al contenitore. Cercare l'indirizzo IP pubblico, nel campo `ipAddress`, da usare con le credenziali nel file Docker per connettersi al contenitore da RTVS.
