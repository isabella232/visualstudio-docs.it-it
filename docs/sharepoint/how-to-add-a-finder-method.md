---
title: 'Procedura: aggiungere un metodo Finder | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7773c2c81527e065652486eb851f3c27828bf76d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767136"
---
# <a name="how-to-add-a-finder-method"></a>Procedura: aggiungere un metodo Finder
  Per abilitare il servizio di integrazione applicativa dei dati (BDC) visualizzare un elenco di entità in una web part o elenco, è necessario creare una *Finder* metodo. Un metodo Finder è un metodo speciale che restituisce una raccolta di istanze di entità. Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Per creare un metodo Finder  
  
1.  Nel **finestra di progettazione di integrazione applicativa dei dati**, scegliere un'entità.  
  
     Per ulteriori informazioni, vedere [procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Nella barra dei menu, scegliere **vista** > **altre finestre** > **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Il **Dettagli metodo di integrazione applicativa dei dati** verrà visualizzata la finestra. Per ulteriori informazioni sul **Dettagli metodo di integrazione applicativa dei dati** finestra, vedere [panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nel **aggiungere un metodo** scegliere **Crea metodo Finder**.  
  
     Visual Studio aggiunge un metodo, un parametro restituito e un descrittore di tipo.  
  
4.  Configurare il descrittore di tipo come un descrittore di tipo raccolta di entità. Per ulteriori informazioni su come creare un descrittore di tipo raccolta di entità, vedere [procedura: definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Non è necessario eseguire questo passaggio se è stato aggiunto un metodo Finder specifico all'entità. Visual Studio utilizza il descrittore di tipo definito nel metodo Finder specifico.  
  
5.  In **Esplora**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**. Per ulteriori informazioni sui file di codice del servizio, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Aggiungere codice al metodo Finder. Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Recupera i dati da un'origine dati.  
  
    -   Restituisce un elenco di entità per il servizio di integrazione applicativa dei dati.  
  
     L'esempio seguente restituisce una raccolta di `Contact` entità utilizzando i dati dal database di esempio AdventureWorks per SQL Server.  
  
    > [!NOTE]  
    >  Sostituire il valore di `ServerName` campo con il nome del server.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Vedere anche
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Progettazione di un modello di integrazione applicativa dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: Definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  