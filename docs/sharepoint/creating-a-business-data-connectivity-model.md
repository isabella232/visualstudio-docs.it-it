---
title: Creazione di un modello di connettività dei dati business | Microsoft Docs
description: Creare un modello BDC (Business Data Connectivity) o personalizzare un modello BDC esistente usando Visual Studio. Ogni SharePoint progetto può contenere un solo modello.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 639b86f0c4b17faf72fb8a74caf9ef6398d770a4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625314"
---
# <a name="create-a-business-data-connectivity-model"></a>Creare un modello di connettività dei dati business
  È possibile creare un modello di integrazione applicativa dei dati (BDC) o personalizzare un modello BDC esistente usando Visual Studio. Ogni SharePoint progetto può contenere un solo modello. Per altre informazioni, vedere [Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Creare un nuovo modello
 Per creare un nuovo modello, creare un **progetto** di modello di integrazione applicativa dei dati o aggiungere un elemento Modello di connettività dati **business** a un SharePoint Project **.**

> [!NOTE]
> È necessario aver [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installato nel computer.

 Visual Studio aggiunge una cartella al progetto. Questa cartella ha il nome specificato per l'elemento Modello di connettività **dati business** nella finestra **di** dialogo Aggiungi nuovo elemento . Se si crea un nuovo progetto **modello** di integrazione applicativa dei dati, Visual Studio la cartella **BdcModel1**.

 Visual Studio aggiunge i file seguenti alla nuova cartella:

|File|Descrizione|
|----------|-----------------|
|File di definizione del modello|Contiene codice XML che definisce entità, metodi, oggetti di sistema Line-of-Business (LOB) e altri metadati che descrivono il modello.<br /><br /> Modificare i metadati in questo file usando Progettazione BDC, **BDC Explorer,** la finestra Dettagli metodo **BDC** e **la finestra** Proprietà.|
|File di codice del servizio entità|Contiene metodi che recuperano, aggiornano ed eliminano istanze dell'entità predefinita.|

 Per definire le proprietà di un'entità, modificare il file di codice dell'entità. Per altre informazioni, vedere [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Per recuperare, aggiornare ed eliminare istanze di un'entità, aggiungere codice al file di codice del servizio entità. Per altre informazioni, vedere [Progettazione di un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

 Quando si compila il progetto, Visual Studio crea un assembly. Assicurarsi di non aggiungere altri elementi al progetto che aggiungono codice  all'assembly del progetto, ad esempio un elemento flusso di lavoro sequenziale o **una web part.** Il codice per tale elemento non verrà eseguito quando si distribuisce la soluzione perché il pacchetto della soluzione non copia l'assembly nella Global Assembly Cache.  Il pacchetto della soluzione distribuisce l'assembly nel database BDC solo SharePoint versione.

> [!NOTE]
> Visual Studio copia l'assembly in entrambi i percorsi nel computer locale quando si esegue il debug del progetto.

## <a name="add-an-existing-model"></a>Aggiungere un modello esistente
 È possibile importare un modello creato usando altri strumenti, ad esempio SharePoint Designer. È possibile scegliere di importare un modello esistente nel progetto nelle situazioni seguenti:

- Per personalizzare un modello già distribuito in un SharePoint server farm.

- Per creare un pacchetto e distribuire un modello esistente in SharePoint server farm.

  In entrambi i casi, i sistemi LOB definiti nel modello importato non sono interessati e continueranno a funzionare come previsto. Per aggiungere un modello esistente a un SharePoint progetto, usare la Visual Studio **finestra di** dialogo Aggiungi elemento esistente. Per altre informazioni, vedere Procedura: Aggiungere un file di modello [BDC esistente a un SharePoint progetto](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  È possibile aggiungere un sistema LOB di tipo .NET Framework assembly al modello importato selezionando un'opzione in **Aggiungi assembly .NET LobSystem**. In questo modo è possibile scrivere codice personalizzato e usare una finestra di progettazione per definire i metadati per il modello importato.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Creare un modello BDC](../sharepoint/how-to-create-a-bdc-model.md)|Illustra come creare un nuovo modello BDC.|
|[Procedura: Aggiungere un file di modello BDC esistente a un SharePoint progetto](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Viene illustrato come importare un modello esistente in un SharePoint progetto.|
|[Procedura: Usare un file di risorse per specificare nomi, proprietà e autorizzazioni localizzati](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Viene descritto come fornire stringhe unite ai metadati del modello quando il modello viene utilizzato da una web part o da una pagina Web.|
|[Procedura: Includere un assembly personalizzato in una funzionalità BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Illustra come includere un assembly personalizzato nella funzionalità.|
