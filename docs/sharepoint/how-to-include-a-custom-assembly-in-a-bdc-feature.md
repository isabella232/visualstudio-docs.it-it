---
title: 'Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 772cdbaca67cc82fc6b7eb2c5ef5adb6508df34a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015261"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati
  Il progetto può fare riferimento agli assembly di altri progetti nella stessa soluzione. Tuttavia, è necessario aggiungere questi assembly al file di funzionalità del progetto utilizzando la finestra di dialogo **Assegna assembly a cui si fa riferimento a agli LobSystem** .

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Per includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati

1. In **Esplora soluzioni**scegliere la cartella che contiene il modello di integrazione applicativa dei dati.

2. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

3. Nella finestra **Proprietà** scegliere la proprietà **assembly** , quindi il pulsante con i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")).

     Verrà visualizzata la finestra **di dialogo Assegna assembly a cui si fa riferimento a agli LobSystem** .

4. Nell'elenco **selezionare un assembly** scegliere l'assembly personalizzato.

    > [!NOTE]
    > Gli assembly vengono visualizzati nella finestra di dialogo **Assegna assembly a cui si fa riferimento a agli LobSystem** solo se è stato aggiunto un riferimento al progetto che contiene l'assembly. Per ulteriori informazioni, vedere [procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

5. Nel gruppo **proprietà riferimento** aprire l'elenco visualizzato per la proprietà **ambito LobSystem** , scegliere il sistema LOB dei metodi che utilizzano l'assembly personalizzato, quindi scegliere il pulsante **OK** .

    > [!NOTE]
    > Per eseguire il debug del codice nell'assembly personalizzato, è necessario aggiungere l'assembly al pacchetto della soluzione. Per altre informazioni, vedere [procedura: aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)
- [Integragte i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
