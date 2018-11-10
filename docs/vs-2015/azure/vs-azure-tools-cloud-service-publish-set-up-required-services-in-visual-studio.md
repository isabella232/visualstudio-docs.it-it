---
title: Preparare la pubblicazione o distribuzione di un servizio Cloud da Visual Studio | Microsoft Docs
description: Scopri le procedure per installare servizi di account di archiviazione e cloud e configurare l'applicazione Azure.
author: ghogen
manager: douge
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: d7643d87f60b953b9c0928571036c7890e4d11f0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002980"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Preparare la pubblicazione o distribuzione di un servizio cloud da Visual Studio

Per pubblicare un progetto servizio cloud, è necessario configurare i servizi seguenti come descritto in questo articolo:

* Oggetto **servizio cloud** per eseguire i ruoli nell'ambiente di Azure, e 
* Oggetto **account di archiviazione** che fornisce l'accesso ai servizi Blob, coda e tabella.

## <a name="create-a-cloud-service"></a>Creare un servizio cloud

Un servizio cloud esegue i ruoli nell'ambiente Azure. È possibile creare un servizio cloud in Visual Studio o tramite il [portale di Azure](https://portal.azure.com/) come descritto nelle sezioni che seguono.

### <a name="create-a-cloud-service-from-visual-studio"></a>Creare un servizio cloud da Visual Studio

1. Con un progetto servizio Cloud creato in precedenza, fare clic sul progetto e scegliere **pubblica**.
1. Se necessario, accedere con l'account Microsoft o aziendale associato alla sottoscrizione di Azure e quindi selezionare **successivo** per passare alle **impostazioni** pagina.
1. Oggetto **Crea servizio Cloud e Account di archiviazione** viene visualizzata la finestra (in caso contrario, selezionare **Crea nuovo** dal **servizio Cloud** elenco).
1. Immettere un nome per il servizio cloud, che fa parte dell'URL e deve essere univoco tra maiuscole e minuscole. Inoltre scegliere un'area o un gruppo di affinità e selezionare un'opzione di replica.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Creare un servizio cloud tramite il portale di Azure

1. Accedere al [portale di Azure](https://portal.azure.com/).
1. Selezionare **servizi Cloud (versione classica)** sul lato sinistro della pagina.
1. Selezionare **+ Aggiungi**, quindi fornire le informazioni necessarie (DNS nome, sottoscrizione, gruppo di risorse e percorso). Non è necessario caricare un pacchetto a questo punto perché farlo in seguito in Visual Studio.
1. Selezionare **Create** per completare il processo.

## <a name="create-a-storage-account"></a>Creare un account di archiviazione

Un account di archiviazione fornisce l'accesso ai servizi Blob, coda e tabella. È possibile creare un account di archiviazione tramite Visual Studio o il [portale di Azure](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Creare un account di archiviazione da Visual Studio

1. Nelle **Esplora soluzioni** con un progetto servizio Cloud creato in precedenza, individuare il **servizi connessi** nodo all'interno di un progetto di ruolo, pulsante destro del mouse e scegliere **Aggiungi servizio connesso**. (In Visual Studio 2015, fare doppio clic il **memorizzazione** nodo e selezionare **crea Account di archiviazione**.)
1. Nel **servizi connessi** elenco visualizzato, selezionare **archiviazione Cloud con archiviazione di Azure**.
1. Nella finestra di dialogo di archiviazione di Azure che viene visualizzato, selezionare **+ Crea nuovo Account di archiviazione**, che consente di visualizzare una finestra di dialogo in cui si specifica la sottoscrizione, un nome per l'account, un prezzo livello, gruppo di risorse e località.
1. Selezionare **Create** dopo aver completato. Il nuovo account di archiviazione viene visualizzato nell'elenco di account di archiviazione disponibili nella sottoscrizione.
1. Selezionare l'account e selezionare **Add**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Creare un account di archiviazione tramite il portale di Azure

1. Accedere al [portale di Azure](https://portal.azure.com/).
1. Selezionare **+ nuovo** in alto a sinistra.
1. Selezionare **memorizzazione** in "Azure Marketplace," quindi **account di archiviazione: blob, file, tabella, coda** dal lato destro.
1. Specificare le informazioni obbligatorie (nome, modello di distribuzione e così via.
1. Selezionare **Create** per completare il processo.

## <a name="configure-your-app-to-use-the-storage-account"></a>Configurare l'app per usare l'account di archiviazione

Dopo aver creato un account di archiviazione, la connessione a esso da Visual Studio automaticamente di aggiornare le configurazioni del servizio per il progetto, inclusi gli URL e le chiavi di accesso.

Se è stato creato un servizio cloud da Visual Studio tramite il **Aggiungi servizio connesso**, è possibile controllare le connessioni aprendo `ServiceConfiguration.Cloud.cscfg` e `ServiceConfiguration.Local.cscfg`.

Se è stato creato un servizio cloud tramite il portale di Azure, seguire la stessa procedura nel [creare un account di archiviazione da Visual Studio](#create-a-storage-account-from-visual-studio) ma selezionare l'account esistente anziché crearne uno nuovo. Visual Studio aggiornerà quindi la configurazione per l'utente.

Per configurare le impostazioni manualmente, usano le pagine delle proprietà in Visual Studio per il ruolo applicabile nel progetto del servizio cloud (ruolo e scegliere **proprietà**). Per altre informazioni, vedere [configurazione di una stringa di connessione a un account di archiviazione](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Informazioni sulle chiavi di accesso

Il portale di Azure vengono visualizzati gli URL che è possibile usare per accedere alle risorse in ognuno dei servizi di archiviazione Azure, nonché le chiavi di accesso primaria e secondaria per l'account. Usare queste chiavi per autenticare le richieste effettuate nei servizi di archiviazione.

La chiave di accesso secondaria fornisce lo stesso accesso all'account di archiviazione come chiave di accesso primaria e viene generata come backup deve essere compromesso la chiave di accesso primaria. Inoltre, è consigliabile rigenerare le chiavi di accesso a intervalli regolari. È possibile modificare un'impostazione della stringa di connessione per usare la chiave secondaria mentre si rigenera la chiave primaria, è possibile modificare in modo che usi la chiave primaria rigenerata mentre si rigenera la chiave secondaria.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla pubblicazione di App in Azure da Visual Studio, vedere [pubblicazione di un servizio Cloud usando gli strumenti di Azure](vs-azure-tools-publishing-a-cloud-service.md).
