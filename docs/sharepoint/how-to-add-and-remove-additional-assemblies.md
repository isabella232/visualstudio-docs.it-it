---
title: 'Procedura: Aggiungere e rimuovere assembly aggiuntivi | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 242ba7fa389a832b1299f00c47ba22a67efc5fbc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873639"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Procedura: Aggiungere e rimuovere assembly aggiuntivi
  Se un pacchetto di SharePoint dipende da altri assembly per dati o funzionalità, è possibile aggiungere gli assembly al pacchetto di soluzione (con estensione wsp). In questo modo, il server SharePoint assicura che siano installati assembly personalizzati con un pacchetto.  
  
 È anche possibile aggiungere e modificare i controlli sicuri e i file di risorse di classe associati con gli assembly.  
  
## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Aggiungere assembly aggiuntivi, controlli sicuri e le risorse di classe  
 È possibile aggiungere altri assembly nel pacchetto della soluzione SharePoint. Distribuire assembly aggiuntivi in una soluzione creata mediante sandbox in global assembly cache, ma nel database di contenuto vengono aggiunti elementi di progetto SharePoint in una soluzione creata mediante sandbox. È anche possibile aggiungere controlli sicuri e le risorse di classe a questi assembly aggiuntivi. Per altre informazioni sui controlli sicuri, vedere [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o "Creazione di una voce di SafeControl" nel [distribuzione di Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Per aggiungere un assembly esistente  
  
1.  Aprire il **Progettazione pacchetti**. Per altre informazioni, vedere [Procedura: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere il **avanzate** scheda.  
  
3.  Scegliere il **Add** pulsante e quindi scegliere **Aggiungi Assembly esistente** dall'elenco.  
  
     Il **Aggiungi Assembly esistente** verrà visualizzata la finestra di dialogo.  
  
4.  Scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")), quindi scegliere l'assembly che si desidera aggiungere. È consigliabile usare un percorso relativo per l'assembly selezionato per scopi di portabilità.  
  
5.  Per il **destinazione di distribuzione**, scegliere il **GlobalAssemblyCache** pulsante di opzione per distribuire l'assembly alla global assembly cache, oppure scegliere il **WebApplication** opzione pulsante per distribuire l'assembly nella cartella WebApplication nel server in cui è in esecuzione SharePoint.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Per aggiungere un assembly dall'output del progetto  
  
1.  Aprire il **Progettazione pacchetti**.  
  
     Per altre informazioni, vedere [Procedura: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere il **avanzate** scheda.  
  
3.  Scegliere il **Add** pulsante e quindi scegliere **Aggiungi Assembly dall'Output del progetto** dall'elenco.  
  
     Il **Aggiungi Assembly dall'Output del progetto** verrà visualizzata la finestra di dialogo.  
  
4.  Nel **progetto di origine** elenco e scegliere il progetto di origine che si desidera aggiungere.  
  
5.  Per il **destinazione di distribuzione**, scegliere il **GlobalAssemblyCache** pulsante di opzione per distribuire l'assembly alla global assembly cache, oppure scegliere il **WebApplication** opzione pulsante per distribuire l'assembly nella cartella WebApplication nel server in cui è in esecuzione SharePoint.  
  
#### <a name="to-add-a-safe-control"></a>Per aggiungere un controllo sicuro  
  
1.  Aprire il **modifica Assembly esistente** nella finestra di dialogo. A tale scopo, aprire la finestra di progettazione del pacchetto, scegliere il **avanzate** scheda, scegliere un assembly e quindi scegliere il **modificare** pulsante.  
  
2.  Nel **controlli sicuri** riquadro, scegliere il **fare clic qui per aggiungere un nuovo elemento** pulsante.  
  
3.  Nel **nome dell'Assembly** colonna, immettere il nome dell'assembly.  
  
4.  Nel **Namespace** colonna, immettere il nome dello spazio dei nomi per il controllo sicuro.  
  
5.  Nel **nome del tipo** colonna, immettere il nome del tipo.  
  
#### <a name="to-add-a-class-resource"></a>Per aggiungere una risorsa di classe  
  
1.  Aprire il **modifica Assembly esistente** nella finestra di dialogo. A tale scopo, aprire la finestra di progettazione del pacchetto, scegliere il **avanzate** scheda, scegliere un assembly e quindi scegliere il **modificare** pulsante.  
  
2.  Nel **classe di risorse** riquadro, scegliere il **fare clic qui per aggiungere un nuovo elemento** pulsante.  
  
3.  Nel **nomefile** colonna, scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) e scegliere la risorsa di classe che si desidera aggiungere.  
  
## <a name="delete-custom-assemblies"></a>Eliminare gli assembly personalizzati  
 È possibile eliminare gli assembly da un pacchetto di SharePoint o eliminare i controlli sicuri e le risorse di classe da assembly esistenti.  
  
#### <a name="to-delete-an-existing-assembly"></a>Per eliminare un assembly esistente  
  
1.  Aprire il **Progettazione pacchetti**. Per altre informazioni, vedere [Procedura: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere il **avanzate** scheda.  
  
3.  Nel **assembly aggiuntivi** riquadro, selezionare l'assembly personalizzato che si desidera eliminare.  
  
4.  Scegliere il **eliminare** pulsante.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Per eliminare un controllo sicuro per un assembly  
  
1.  Aprire il **modifica Assembly esistente** nella finestra di dialogo. A tale scopo, aprire la finestra di progettazione del pacchetto, scegliere il **avanzate** scheda, scegliere un assembly e quindi scegliere il **modificare** pulsante.  
  
2.  Scegliere il controllo sicuro che si desidera eliminare.  
  
3.  Scegliere il tasto CANC.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Per eliminare una risorsa di classe per un assembly  
  
1.  Aprire il **modifica Assembly esistente** nella finestra di dialogo. A tale scopo, aprire la finestra di progettazione del pacchetto, scegliere il **avanzate** scheda, scegliere un assembly e quindi scegliere il **modificare** pulsante.  
  
2.  Scegliere la risorsa di classe che si desidera eliminare.  
  
3.  Scegliere il tasto CANC.  
  
## <a name="see-also"></a>Vedere anche
 [Creare funzionalità di SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Procedura: Personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: Aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
