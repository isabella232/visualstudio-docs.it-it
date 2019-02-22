---
title: 'Procedura: Aggiungere un metodo Creator | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1c1596213b618ba67cd4bf1406f63c0754fd9b96
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619316"
---
# <a name="how-to-add-a-creator-method"></a>Procedura: Aggiungere un metodo Creator
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
- [Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)
