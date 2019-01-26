---
title: 'Procedura: Aggiungere un metodo Deleter | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cad4de5ed1b31d02d9136b5ec2b46be71f54fea4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870883"
---
# <a name="how-to-add-a-deleter-method"></a>Procedura: Aggiungere un metodo Deleter
  È possibile abilitare un utente finale eliminare un record di dati da un elenco esterno in un sito di SharePoint tramite l'aggiunta di un metodo Deleter per il modello. Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-deleter-method"></a>Per creare un metodo Deleter  
  
1. Nel **finestra di progettazione integrazione applicativa dei dati**, scegliere un'entità.  
  
2. Nella barra dei menu, scegliere **View** > **Other Windows** > **Dettagli metodo BDC**.  
  
    Il **Dettagli metodo BDC** verrà visualizzata la finestra. Per altre informazioni su questa finestra, vedere [Cenni preliminari sugli strumenti di progettazione di modelli di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. Nel **aggiungere un metodo** casella di riepilogo **creare un metodo Deleter**.  
  
    Visual Studio aggiunge i seguenti elementi al modello. Questi elementi vengono visualizzati nei **Dettagli metodo BDC** finestra.  
  
   - Un metodo denominato **Elimina**.  
  
   - Un parametro di input per il metodo.  
  
   - Un descrittore di tipo per il parametro.  
  
   - Un'istanza del metodo per il metodo.  
  
     Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**.  
  
    File di codice servizio dell'entità viene aperto nell'Editor del codice. Per altre informazioni sui file di codice servizio dell'entità, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Aggiungere codice al metodo Deleter per eliminare un record. L'esempio seguente elimina una voce da un ordine di vendita tramite il database di esempio AdventureWorks per SQL Server.  
  
   > [!NOTE]  
   >  Il metodo in questo esempio usa due parametri di input.  
  
   > [!NOTE]  
   >  Sostituire il valore del `ServerName` campo con il nome del server.  
  
    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>Vedere anche
 [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)  
