---
title: 'Procedura: Aggiungere e rimuovere altri assembly | Microsoft Docs'
description: Informazioni su come aggiungere e rimuovere altri assembly nei pacchetti SharePoint soluzione. Aggiungere o eliminare anche controlli sicuri e risorse di classe.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 113b881759f523d7b2f583fb33b25d4186ff30e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131066"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Procedura: Aggiungere e rimuovere assembly aggiuntivi
  Se un SharePoint pacchetto dipende da altri assembly per funzionalità o dati, è possibile aggiungere gli assembly al pacchetto della soluzione (con estensione wsp). In questo modo, SharePoint server verifica che gli assembly personalizzati siano installati con un pacchetto.

 È anche possibile aggiungere e modificare i controlli sicuri e i file di risorse della classe associati agli assembly.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Aggiungere altri assembly, controlli sicuri e risorse di classe
 È possibile aggiungere altri assembly nel pacchetto SharePoint soluzione. Assembly aggiuntivi in una soluzione sandbox vengono distribuiti nella Global Assembly Cache, ma SharePoint elementi di progetto in una soluzione sandbox vengono aggiunti al database del contenuto. È anche possibile aggiungere controlli sicuri e risorse di classe a questi assembly aggiuntivi. Per altre informazioni sui controlli sicuri, vedere Providing [Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o "Creating a SafeControl Entry" in [Deploying Web part in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

#### <a name="to-add-an-existing-assembly"></a>Per aggiungere un assembly esistente

1. Aprire Progettazione **pacchetti**. Per altre informazioni, vedere [Procedura: Personalizzare un pacchetto SharePoint soluzione](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Scegliere la **scheda** Avanzate.

3. Scegliere il **pulsante Aggiungi** e quindi Aggiungi **assembly esistente** dall'elenco.

     Verrà **visualizzata la finestra di dialogo Aggiungi assembly** esistente .

4. Scegliere i puntini di sospensione (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) e quindi scegliere l'assembly da aggiungere. È consigliabile usare un percorso relativo all'assembly selezionato ai fini della portabilità.

5. Per Destinazione distribuzione **scegliere** il pulsante di opzione **GlobalAssemblyCache** per distribuire l'assembly nella Global Assembly Cache oppure scegliere il pulsante di opzione **WebApplication** per distribuire l'assembly nella cartella WebApplication nel server che esegue SharePoint.

#### <a name="to-add-an-assembly-from-project-output"></a>Per aggiungere un assembly dall'output del progetto

1. Aprire Progettazione **pacchetti**.

     Per altre informazioni, vedere [Procedura: Personalizzare un pacchetto SharePoint soluzione .](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)

2. Scegliere la **scheda** Avanzate.

3. Scegliere il **pulsante Aggiungi** e quindi Aggiungi assembly dall'Project **output** dall'elenco.

     Verrà visualizzata la finestra di dialogo Aggiungi assembly **Project output.**

4. **Nell'elenco Origine Project** e scegliere il progetto di origine da aggiungere.

5. Per Destinazione distribuzione **scegliere** il pulsante di opzione **GlobalAssemblyCache** per distribuire l'assembly nella Global Assembly Cache oppure scegliere il pulsante di opzione **WebApplication** per distribuire l'assembly nella cartella WebApplication nel server che esegue SharePoint.

#### <a name="to-add-a-safe-control"></a>Per aggiungere un controllo sicuro

1. Aprire la **finestra di dialogo Modifica assembly** esistente. A tale scopo, aprire Progettazione pacchetti, scegliere la **scheda** Avanzate, scegliere un assembly e quindi scegliere **il pulsante** Modifica.

2. Nel riquadro **Cassaforte controlli** fare clic sul pulsante Fare clic qui per aggiungere un **nuovo elemento.**

3. Nella colonna **Nome assembly** immettere il nome dell'assembly.

4. Nella colonna **Spazio** dei nomi immettere il nome dello spazio dei nomi per il controllo sicuro.

5. Nella colonna **Nome tipo** immettere il nome del tipo.

#### <a name="to-add-a-class-resource"></a>Per aggiungere una risorsa di classe

1. Aprire la **finestra di dialogo Modifica assembly** esistente. A tale scopo, aprire Progettazione pacchetti, scegliere la **scheda** Avanzate, scegliere un assembly e quindi scegliere **il pulsante** Modifica.

2. Nel riquadro **Risorse classe** scegliere il pulsante Fare clic qui per aggiungere un **nuovo elemento.**

3. Nella colonna **Nome file** scegliere i puntini di sospensione ( ASP.NET ![Mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) e scegliere la risorsa di classe da aggiungere.

## <a name="delete-custom-assemblies"></a>Eliminare assembly personalizzati
 È possibile eliminare assembly da un pacchetto SharePoint o eliminare controlli sicuri e risorse di classe da assembly esistenti.

#### <a name="to-delete-an-existing-assembly"></a>Per eliminare un assembly esistente

1. Aprire Progettazione **pacchetti**. Per altre informazioni, vedere [Procedura: Personalizzare un pacchetto SharePoint soluzione .](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)

2. Scegliere la **scheda** Avanzate.

3. Nel **riquadro Assembly aggiuntivi** scegliere l'assembly personalizzato da eliminare.

4. Fare clic sul pulsante **Elimina**.

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Per eliminare un controllo sicuro per un assembly

1. Aprire la **finestra di dialogo Modifica assembly** esistente. A tale scopo, aprire Progettazione pacchetti, scegliere la **scheda** Avanzate, scegliere un assembly e quindi scegliere **il pulsante** Modifica.

2. Scegliere il controllo sicuro da eliminare.

3. Scegliere il tasto Canc.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Per eliminare una risorsa di classe per un assembly

1. Aprire la **finestra di dialogo Modifica assembly** esistente. A tale scopo, aprire Progettazione pacchetti, scegliere la **scheda** Avanzate, scegliere un assembly e quindi scegliere **il pulsante** Modifica.

2. Scegliere la risorsa di classe che si vuole eliminare.

3. Scegliere il tasto Canc.

## <a name="see-also"></a>Vedi anche
- [Creare SharePoint funzionalità](../sharepoint/creating-sharepoint-features.md)
- [Procedura: Personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Procedura: Aggiungere e rimuovere elementi per SharePoint funzionalità](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
