---
title: 'Procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2015 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46b48370847cbb2cf8b171342aff9baf38c40a22
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295556"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ecco come eseguire l'aggiornamento dell'estensione.  
  
> [!IMPORTANT]
> Se si intende mantenere una versione della soluzione di estensione per una versione precedente di Visual Studio, assicurarsi di creare una copia prima di aggiornarla. Potrebbe essere difficile ripristinare lo stato precedente della versione aggiornata.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Per aggiornare una soluzione di estendibilità  
  
1. Utilizzando la copia che si desidera aggiornare, aprirla nella nuova versione. Si può notare che l'aggiornamento non è reversibile.  
  
2. Al termine dell'aggiornamento, modificare il percorso del programma esterno con la nuova versione di devenv. exe. Fare clic con il pulsante destro del mouse sul nodo del progetto nella **Esplora soluzioni**, quindi scegliere **Proprietà**. Nella scheda **debug** trovare la casella di testo **Avvia programma esterno** e modificare il percorso di devenv. exe nel percorso di Visual Studio 2015, che dovrebbe avere un aspetto simile al seguente:  
  
     **%Programmi%\Microsoft Visual Studio 14.0 \ Common7\IDE\devenv.exe**  
  
3. Aggiungere un riferimento a Microsoft. VisualStudio. Shell. 14.0. dll. Fare clic con il pulsante destro del mouse sul nodo del progetto nella **Esplora soluzioni** , quindi scegliere **Aggiungi/riferimento**. Selezionare la scheda **estensioni** , quindi selezionare **Microsoft. VisualStudio. Shell. 14.0**.  
  
4. Compilare la soluzione. I file compilati vengono distribuiti in:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nome dell'autore\>\\< nome del progetto** \>\\<\>versione del progetto \\.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Per aggiornare un progetto di estendibilità agli assembly di riferimento NuGet VS SDK  
  
1. Determinare gli assembly di riferimento di Visual Studio SDK necessari per il progetto.  In **Esplora soluzioni**espandere il nodo **riferimenti** del progetto ed esaminare l'elenco dei riferimenti al progetto.  Gli assembly di riferimento di VS SDK avranno il prefisso **Microsoft. VisualStudio** nel nome, ad esempio Microsoft. VisualStudio. Shell. 14.0.  
  
2. Rimuovere gli assembly di riferimento di Visual Studio SDK dal progetto selezionandoli, fare clic con il pulsante destro del mouse e **rimuovere**.  
  
3. Aggiungere le versioni NuGet degli assembly di riferimento di Visual Studio SDK.  Nel nodo **Esplora soluzioni References** aprire la pagina **Gestisci pacchetti NuGet...** dialogo.  Per altre informazioni su questa finestra di dialogo, vedere [gestire i pacchetti NuGet usando la finestra di dialogo](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio). Gli assembly di riferimento di Visual Studio SDK sono pubblicati in [NuGet.org](https://www.nuget.org/) da [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4. Usando **NuGet.org** come **origine del pacchetto**, cercare il nome del pacchetto NuGet che corrisponde all'assembly di riferimento desiderato (ad esempio: Microsoft. VisualStudio. Shell. 14.0) e installarlo nel progetto.  NuGet può aggiungere più assembly di riferimento per soddisfare le dipendenze dell'assembly iniziale.  
  
     Se si preferisce, è possibile aggiungere contemporaneamente tutti gli assembly di riferimento di Visual Studio SDK installando il [pacchetto meta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)SDK di Visual Studio.  
  
5. È anche possibile passare all'uso della versione NuGet degli strumenti di compilazione di Visual Studio SDK. Questo pacchetto NuGet è [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) e, una volta aggiunto al progetto, includerà i file di destinazione e gli strumenti necessari per consentire la compilazione del progetto di estendibilità in un computer in cui non è installato Visual Studio SDK.  
  
> [!NOTE]
> Non è necessario aggiornare i progetti di estendibilità esistenti per usare gli strumenti e gli assembly di riferimento NuGet.  Possono continuare a compilare usando gli assembly di riferimento e gli strumenti installati con Visual Studio SDK.
