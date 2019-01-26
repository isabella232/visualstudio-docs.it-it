---
title: 'Procedura: Aggiungere un metodo Finder | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ae5b1dfca8a083f12aa05d96378c3df348766a0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872885"
---
# <a name="how-to-add-a-finder-method"></a>Procedura: Aggiungere un metodo Finder
  Per abilitare il servizio di integrazione applicativa dei dati (BDC) visualizzare un elenco di entità in una web part o elenco, è necessario creare un *Finder* (metodo). Un metodo Finder è un metodo speciale che restituisce una raccolta di istanze di entità. Per altre informazioni, vedere [progettare un Business Data Connectivity Model](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Per creare un metodo Finder  
  
1. Nel **finestra di progettazione integrazione applicativa dei dati**, scegliere un'entità.  
  
    Per altre informazioni, vedere [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2. Nella barra dei menu, scegliere **View** > **Other Windows** > **Dettagli metodo BDC**.  
  
    Il **Dettagli metodo BDC** verrà visualizzata la finestra. Per altre informazioni sul **Dettagli metodo BDC** finestra, vedere [Cenni preliminari sugli strumenti di progettazione di modelli di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. Nel **aggiungere un metodo** casella di riepilogo **Crea metodo Finder**.  
  
    Visual Studio aggiunge un metodo, un parametro restituito e un descrittore di tipo.  
  
4. Configurare il descrittore di tipo come un descrittore di tipo raccolta di entità. Per altre informazioni su come creare un descrittore di tipo raccolta di entità, vedere [come: Definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
   > [!NOTE]  
   >  Non è necessario eseguire questo passaggio se è stato aggiunto un metodo Finder specifico per l'entità. Visual Studio Usa il descrittore di tipo definito nel metodo Finder specifico.  
  
5. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**. Per altre informazioni sui file di codice del servizio, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6. Aggiungere codice al metodo Finder. Mediante il codice vengono effettuate le seguenti attività:  
  
   - Recupera i dati da un'origine dati.  
  
   - Restituisce un elenco di entità per il servizio di integrazione applicativa dei dati.  
  
     L'esempio seguente restituisce una raccolta di `Contact` entità usando i dati dal database di esempio AdventureWorks per SQL Server.  
  
   > [!NOTE]  
   >  Sostituire il valore del `ServerName` campo con il nome del server.  
  
    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Vedere anche
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)  
