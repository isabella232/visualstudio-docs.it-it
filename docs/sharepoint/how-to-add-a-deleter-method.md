---
title: 'Procedura: aggiungere un metodo Deleter | Documenti Microsoft'
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
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 02a6daf7a3155113ecd06d991b337b54fb0d7cd4
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768131"
---
# <a name="how-to-add-a-deleter-method"></a>Procedura: aggiungere un metodo Deleter
  È possibile abilitare un utente finale eliminare un record dei dati da un elenco esterno in un sito di SharePoint tramite l'aggiunta di un metodo Deleter al modello. Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-deleter-method"></a>Per creare un metodo Deleter  
  
1.  Nel **finestra di progettazione di integrazione applicativa dei dati**, scegliere un'entità.  
  
2.  Nella barra dei menu, scegliere **vista** > **altre finestre** > **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Il **Dettagli metodo di integrazione applicativa dei dati** verrà visualizzata la finestra. Per ulteriori informazioni su questa finestra, vedere [panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nel **aggiungere un metodo** scegliere **creare un metodo Deleter**.  
  
     Visual Studio aggiunge i seguenti elementi al modello. Questi elementi vengono visualizzati nel **Dettagli metodo di integrazione applicativa dei dati** finestra.  
  
    -   Un metodo denominato **eliminare**.  
  
    -   Un parametro di input per il metodo.  
  
    -   Un descrittore di tipo per il parametro.  
  
    -   Un'istanza del metodo per il metodo.  
  
     Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  In **Esplora**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**.  
  
     File di codice servizio dell'entità verrà aperto nell'Editor di codice. Per ulteriori informazioni sui file di codice servizio dell'entità, vedere [creazione di un modello di connettività dei dati di Business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Aggiungere codice al metodo Deleter per eliminare un record. Nell'esempio seguente elimina un elemento di riga da un ordine di vendita tramite il database di esempio AdventureWorks per SQL Server.  
  
    > [!NOTE]  
    >  Il metodo in questo esempio utilizza due parametri di input.  
  
    > [!NOTE]  
    >  Sostituire il valore di `ServerName` campo con il nome del server.  
  
     [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>Vedere anche
 [Progettazione di un modello di integrazione applicativa dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: Definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  