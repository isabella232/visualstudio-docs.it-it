---
title: 'Procedura: aggiungere un metodo Creator | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a8aa49416a826e5100932b4741d3e536a9d2f37d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897342"
---
# <a name="how-to-add-a-creator-method"></a>Procedura: aggiungere un metodo Creator
  Un metodo Creator aggiunge nuovi dati all'origine dati di un'entità. Il servizio di integrazione applicativa dei dati (BDC) chiama questo metodo quando gli utenti scelgono il **nuovo elemento** pulsante il **della barra multifunzione** di un elenco che si basa sul modello. Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Per aggiungere un metodo Creator  
  
1. Nel **finestra di progettazione integrazione applicativa dei dati**, scegliere un'entità.  
  
2. Nella barra dei menu, scegliere **View** > **Other Windows** >**Dettagli metodo BDC**.  
  
    Il **Dettagli metodo BDC** verrà visualizzata la finestra. Per altre informazioni su tale finestra, vedere [Cenni preliminari sugli strumenti di progettazione di modelli di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. Nel **aggiungere un metodo** casella di riepilogo **Crea metodo Creator**.  
  
    Visual Studio aggiunge i seguenti elementi al modello e tali elementi vengono visualizzati nei **Dettagli metodo BDC** finestra.  
  
   - Un metodo denominato **Create**.  
  
   - Un parametro di input per il metodo.  
  
   - Un parametro restituito del metodo.  
  
   - Descrittori per i parametri di tipo.  
  
   - Un'istanza del metodo per il metodo.  
  
     Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida del servizio file di codice che è stato generato per l'entità e quindi scegliere **Visualizza codice**.  
  
    File di codice servizio dell'entità viene aperto nell'Editor del codice. Per altre informazioni sui file di codice servizio dell'entità, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Aggiungere codice al metodo di creazione che aggiunge dati all'origine dati. L'esempio seguente aggiunge un contatto per il database di esempio AdventureWorks per SQL Server.  
  
   > [!NOTE]  
   >  Sostituire il valore del `ServerName` campo con il nome del server.  
  
    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Vedere anche
 [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  
