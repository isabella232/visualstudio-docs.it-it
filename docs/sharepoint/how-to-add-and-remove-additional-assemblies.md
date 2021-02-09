---
title: 'Procedura: aggiungere e rimuovere assembly aggiuntivi | Microsoft Docs'
description: Informazioni su come aggiungere e rimuovere assembly aggiuntivi nei pacchetti della soluzione SharePoint. Aggiungere o eliminare anche controlli e risorse di classe sicuri.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc672a8a0ff7edd66504b5ecbf48e622fad085ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923620"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Procedura: aggiungere e rimuovere assembly aggiuntivi
  Se un pacchetto di SharePoint dipende da altri assembly per la funzionalità o i dati, è possibile aggiungere gli assembly al pacchetto della soluzione (con estensione wsp). In questo modo, il server SharePoint verifica che gli assembly personalizzati vengano installati con un pacchetto.

 È anche possibile aggiungere e modificare i controlli Safe e i file di risorse di classe associati agli assembly.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Aggiungere altri assembly, controlli sicuri e risorse di classe
 È possibile aggiungere altri assembly al pacchetto della soluzione SharePoint. Gli assembly aggiuntivi in una soluzione creata mediante sandbox vengono distribuiti nel Global Assembly Cache, ma gli elementi del progetto SharePoint in una soluzione creata mediante sandbox vengono aggiunti al database del contenuto. È anche possibile aggiungere controlli sicuri e risorse di classe a questi assembly aggiuntivi. Per ulteriori informazioni sui controlli sicuri, vedere la sezione relativa alla creazione di [pacchetti e informazioni sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o nella sezione relativa alla creazione di una voce SafeControl in [distribuzione di Web part in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

#### <a name="to-add-an-existing-assembly"></a>Per aggiungere un assembly esistente

1. Aprire **Progettazione pacchetti**. Per ulteriori informazioni, vedere [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Scegliere la scheda **Avanzate** .

3. Scegliere il pulsante **Aggiungi** , quindi scegliere **Aggiungi assembly esistente** dall'elenco.

     Verrà visualizzata la finestra di dialogo **Aggiungi assembly esistente** .

4. Scegliere i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")), quindi scegliere l'assembly che si desidera aggiungere. Per finalità di portabilità, è consigliabile usare un percorso relativo all'assembly selezionato.

5. Per la **destinazione della distribuzione**, scegliere il pulsante di opzione **GlobalAssemblyCache** per distribuire l'assembly nella global assembly cache o scegliere il pulsante di opzione **applicazione** Web per distribuire l'assembly nella cartella WebApplication nel server in cui è in esecuzione SharePoint.

#### <a name="to-add-an-assembly-from-project-output"></a>Per aggiungere un assembly dall'output del progetto

1. Aprire **Progettazione pacchetti**.

     Per ulteriori informazioni, vedere [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Scegliere la scheda **Avanzate** .

3. Scegliere il pulsante **Aggiungi** , quindi scegliere **Aggiungi assembly dall'output del progetto** dall'elenco.

     Verrà visualizzata la finestra **di dialogo Aggiungi assembly da output progetto** .

4. Nell'elenco **progetto di origine** , scegliere il progetto di origine che si desidera aggiungere.

5. Per la **destinazione della distribuzione**, scegliere il pulsante di opzione **GlobalAssemblyCache** per distribuire l'assembly nella global assembly cache o scegliere il pulsante di opzione **applicazione** Web per distribuire l'assembly nella cartella WebApplication nel server in cui è in esecuzione SharePoint.

#### <a name="to-add-a-safe-control"></a>Per aggiungere un controllo sicuro

1. Aprire la finestra di dialogo **modifica assembly esistente** . A tale scopo, aprire Progettazione pacchetti, scegliere la scheda **Avanzate** , scegliere un assembly, quindi scegliere il pulsante **modifica** .

2. Nel riquadro **controlli sicuri** scegliere il pulsante **fare clic qui per aggiungere un nuovo elemento** .

3. Nella colonna **nome assembly** immettere il nome dell'assembly.

4. Nella colonna **spazio dei nomi** immettere il nome dello spazio dei nomi per il controllo sicuro.

5. Nella colonna **nome tipo** immettere il nome del tipo.

#### <a name="to-add-a-class-resource"></a>Per aggiungere una risorsa di classe

1. Aprire la finestra di dialogo **modifica assembly esistente** . A tale scopo, aprire Progettazione pacchetti, scegliere la scheda **Avanzate** , scegliere un assembly, quindi scegliere il pulsante **modifica** .

2. Nel riquadro **risorse della classe** scegliere il pulsante **fare clic qui per aggiungere un nuovo elemento** .

3. Nella colonna **nome file** scegliere i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) e scegliere la risorsa di classe che si desidera aggiungere.

## <a name="delete-custom-assemblies"></a>Elimina assembly personalizzati
 È possibile eliminare gli assembly da un pacchetto di SharePoint o eliminare i controlli sicuri e le risorse di classe dagli assembly esistenti.

#### <a name="to-delete-an-existing-assembly"></a>Per eliminare un assembly esistente

1. Aprire **Progettazione pacchetti**. Per ulteriori informazioni, vedere [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Scegliere la scheda **Avanzate** .

3. Nel riquadro **assembly aggiuntivi** scegliere l'assembly personalizzato che si desidera eliminare.

4. Fare clic sul pulsante **Elimina**.

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Per eliminare un controllo sicuro per un assembly

1. Aprire la finestra di dialogo **modifica assembly esistente** . A tale scopo, aprire Progettazione pacchetti, scegliere la scheda **Avanzate** , scegliere un assembly, quindi scegliere il pulsante **modifica** .

2. Scegliere il controllo sicuro che si desidera eliminare.

3. Scegliere il tasto CANC.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Per eliminare una risorsa di classe per un assembly

1. Aprire la finestra di dialogo **modifica assembly esistente** . A tale scopo, aprire Progettazione pacchetti, scegliere la scheda **Avanzate** , scegliere un assembly, quindi scegliere il pulsante **modifica** .

2. Scegliere la risorsa di classe che si desidera eliminare.

3. Scegliere il tasto CANC.

## <a name="see-also"></a>Vedi anche
- [Creazione di funzionalità di SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Procedura: Personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: aggiungere e rimuovere elementi nelle funzionalità di SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
