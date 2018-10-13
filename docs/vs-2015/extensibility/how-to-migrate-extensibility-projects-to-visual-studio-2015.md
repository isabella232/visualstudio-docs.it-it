---
title: 'Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2015 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff64d4578a0add2e027af8f6bf93c01e0f32ce24
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282282"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ecco come eseguire l'aggiornamento dell'estensione.  
  
> [!IMPORTANT]
>  Se si prevede di gestire una versione della soluzione di estensione per una versione precedente di Visual Studio, assicurarsi di creare una copia prima di aggiornarlo. Potrebbe essere difficile restituire la versione aggiornata allo stato precedente.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Per eseguire l'aggiornamento di una soluzione di estendibilità  
  
1.  Usando la copia si desidera aggiornare, aprirlo nella nuova versione. Si viene avvisati che l'aggiornamento non è reversibile.  
  
2.  Al termine dell'aggiornamento, modificare il percorso del programma esterno per la nuova versione di devenv.exe. Fare clic sul nodo del progetto nel **Esplora soluzioni**, quindi scegliere **proprietà**. Nel **Debug** scheda, la casella di testo da trovare **Avvia programma esterno** e modificare il percorso di devenv.exe sul percorso di Visual Studio 2015, che dovrebbe essere simile al seguente:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Aggiungere un riferimento a Microsoft.VisualStudio.Shell.14.0.dll. (Fare clic sul nodo del progetto nel **Esplora soluzioni** e quindi scegliere **aggiungere-Reference**. Selezionare il **Extensions** scheda e quindi controllare **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Compilare la soluzione. I file compilati vengono distribuiti per:  
  
     **%LocalAppData%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nome di autore\>\\< nome progetto\>\\< versione progetto\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Per aggiornare un progetto di estensibilità per gli assembly di riferimento di NuGet di Visual Studio SDK  
  
1.  Determinare gli assembly di riferimento di Visual Studio SDK che nel progetto è richiesta.  Nelle **Esplora soluzioni**, espandere il progetto **riferimenti** nodo ed esaminare l'elenco di riferimenti al progetto.  Gli assembly di riferimenti di Visual Studio SDK avranno il prefisso **Microsoft.VisualStudio** nel nome (ad esempio: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Rimuovere gli assembly di riferimento di Visual Studio SDK dal progetto selezionandole facendo clic con il pulsante destro e **rimuovere**.  
  
3.  Aggiungere le versioni NuGet degli assembly di riferimento di Visual Studio SDK.  Mentre si trovano ancora nella **riferimenti di Esplora soluzioni** nodo, aprire il **Gestisci pacchetti NuGet...** finestra di dialogo.  Per altre informazioni su questa finestra di dialogo, vedere [la gestione di pacchetti NuGet mediante la finestra di dialogo](http://docs.nuget.org/Consume/Package-Manager-Dialog). Gli assembly di riferimento di Visual Studio SDK sono stati pubblicati nel [nuget.org](http://www.nuget.org) dal [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Usando **nuget.org** come le **origine pacchetto**, cercare il nome del pacchetto NuGet che corrisponde all'assembly di riferimento desiderato (ad esempio: Microsoft.VisualStudio.Shell.14.0) e installarlo nel progetto.  NuGet può aggiungere più assembly di riferimento per soddisfare le dipendenze dell'assembly iniziale.  
  
     Se si preferisce, è possibile aggiungere contemporaneamente tutti gli assembly di riferimento di Visual Studio SDK mediante l'installazione di Visual Studio SDK [metapacchetto](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  È anche possibile passare all'uso della versione di NuGet degli strumenti di compilazione di Visual Studio SDK. Il pacchetto NuGet [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) e una volta aggiunto a includere gli strumenti necessari e i file per consentire la compilazione del progetto di estendibilità in un computer senza installato il SDK di Visual Studio di destinazione del progetto di.  
  
> [!NOTE]
>  Non è necessario aggiornare i progetti di estendibilità esistenti per l'uso di strumenti e gli assembly di riferimento di NuGet.  È possibile continuare a compilare usando gli assembly di riferimento e gli strumenti installati con il SDK di Visual Studio.

