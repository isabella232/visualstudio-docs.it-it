---
title: 'Procedura: Includere un assembly personalizzato in una funzionalità BDC | Microsoft Docs'
description: Includere assembly personalizzati in una funzionalità BDC (Business Data Connectivity) in modo che il progetto possa fare riferimento ad assembly di altri progetti nella stessa soluzione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 14026e6de7a376e4548723b4b540d314e499bbf1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092995"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Procedura: Includere un assembly personalizzato in una funzionalità BDC
  Il progetto può fare riferimento ad assembly da altri progetti nella stessa soluzione. Tuttavia, è necessario aggiungere questi assembly al file di funzionalità del progetto usando la finestra di dialogo Assegna assembly a cui si fa riferimento **a LobSystems** .

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Per includere un assembly personalizzato in una funzionalità BDC (Business Data Connectivity)

1. In **Esplora soluzioni** scegliere la cartella che contiene il modello BDC.

2. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

3. Nella finestra **Proprietà** scegliere la proprietà **Assembly** e quindi il pulsante con i puntini di sospensione ( ASP.NET ![puntini di sospensione di Progettazione dispositivi mobili](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")).

     Verrà **visualizzata la finestra di dialogo Assign referenced assemblies to LobSystems** (Assegna assembly a cui si fa riferimento a LobSystems).

4. **Nell'elenco Selezionare un assembly** scegliere l'assembly personalizzato.

    > [!NOTE]
    > Gli assembly vengono visualizzati nella finestra di dialogo Assegna assembly a cui si fa riferimento a **LobSystems** solo se è stato aggiunto un riferimento al progetto che contiene l'assembly. Per altre informazioni, vedere [Procedura: Aggiungere o rimuovere riferimenti tramite](/previous-versions/wkze6zky(v=vs.140))la finestra di dialogo Aggiungi riferimento .

5. Nel gruppo **Proprietà** riferimento aprire l'elenco visualizzato per la proprietà **Ambito lobSystem,** scegliere il sistema LOB dei metodi che usano l'assembly personalizzato e quindi scegliere **il pulsante OK.**

    > [!NOTE]
    > Per eseguire il debug del codice nell'assembly personalizzato, è necessario aggiungere l'assembly al pacchetto della soluzione. Per altre informazioni, [vedere Procedura: Aggiungere e rimuovere assembly aggiuntivi.](../sharepoint/how-to-add-and-remove-additional-assemblies.md)

## <a name="see-also"></a>Vedi anche
- [Procedura: Usare un file di risorse per specificare nomi, proprietà e autorizzazioni localizzati](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Procedura: Aggiungere un file di modello BDC esistente a un SharePoint progetto](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Creare un modello di connettività dei dati aziendali](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: Creare un modello BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)