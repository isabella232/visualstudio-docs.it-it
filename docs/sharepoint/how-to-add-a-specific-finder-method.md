---
title: 'Procedura: Aggiungere un metodo Finder specifico | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 163badc38ba4037729e29d013c98e0b733c9eaf9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913465"
---
# <a name="how-to-add-a-specific-finder-method"></a>Procedura: Aggiungere un metodo Finder specifico
  È possibile restituire un'istanza singola entità tramite la creazione di un *Finder specifico* (metodo). Il servizio di integrazione applicativa dei dati (BDC) esegue il metodo Finder specifico quando un utente sceglie un'entità in una web part dei dati di business o un elenco esterno. Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Per creare un metodo Finder specifico
  
1. Nel **finestra di progettazione integrazione applicativa dei dati**, scegliere un'entità.  
  
    Per informazioni su come aggiungere un'entità per il **finestra di progettazione integrazione applicativa dei dati** in Visual Studio, vedere [come: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2. Nella barra dei menu, scegliere **View** > **Other Windows**, **Dettagli metodo BDC**.  
  
    Il **Dettagli metodo BDC** verrà visualizzata la finestra. Per altre informazioni su tale finestra, vedere [Cenni preliminari sugli strumenti di progettazione di modelli di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. Nel **aggiungere un metodo** casella di riepilogo **Crea metodo Finder specifico**.  
  
    Visual Studio aggiunge i seguenti elementi al modello. Questi elementi vengono visualizzati nei **Dettagli metodo BDC** finestra.  
  
   - Un metodo.  
  
   - Un parametro di input per il metodo.  
  
   - Un parametro restituito del metodo.  
  
   - Un descrittore di tipo per ogni parametro.  
  
   - Un'istanza del metodo per il metodo.  
  
     Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. Aprire Visual Studio **proprietà** finestra.  
  
5. Configurare il descrittore di tipo del parametro restituito come un descrittore di tipo di entità. Per informazioni su come creare un descrittore di tipo di entità, vedere [come: Definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
   > [!NOTE]  
   >  Si è autorizzati a eseguire questo passaggio se è stato aggiunto un metodo Finder per l'entità. Visual Studio Usa il descrittore di tipo definito nel metodo Finder.  
  
   > [!NOTE]  
   >  Se il campo dell'identificatore del tipo di entità rappresenta un campo in una tabella di database che viene generato automaticamente, impostare il **Read-only** proprietà del campo identificatore **True**.  
  
6. Nel **Dettagli metodo** finestra, scegliere l'istanza del metodo del metodo.  
  
7. Nel **finestra delle proprietà**, impostare il **nome parametro restituito** proprietà sul nome del parametro restituito del metodo. Per altre informazioni sulle proprietà di istanza di metodo, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**.  
  
    File di codice servizio dell'entità viene aperto nell'Editor del codice. Per altre informazioni sui file di codice servizio dell'entità, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Aggiungere codice al metodo Finder specifico. Mediante il codice vengono effettuate le seguenti attività:  
  
   - Recupera un record da un'origine dati.  
  
   - Restituisce un'entità per il servizio di integrazione applicativa dei dati.  
  
     L'esempio seguente restituisce un contatto da database di esempio AdventureWorks per SQL Server.  
  
     > [!NOTE]  
     >  Sostituire il valore del `ServerName` campo con il nome del server.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>Vedere anche
 [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)  
