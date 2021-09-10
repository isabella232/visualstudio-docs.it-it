---
title: Gestione delle proprietà di progetti e soluzioni
description: Questo articolo descrive come gestire le proprietà di progetti e soluzioni in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964502"
---
# <a name="managing-project-and-solution-properties"></a>Gestione delle proprietà di progetti e soluzioni

## <a name="project-options"></a>Opzioni del progetto

Le opzioni del progetto sono specifiche di ogni progetto e influiscono sul modo in cui il progetto viene scritto, compilato ed eseguito. A Visual Studio per Mac preferenze che sono impostazioni specifiche dell'utente, le opzioni di progetto vengono archiviate nel file di progetto (con estensione csproj), in modo che altri sviluppatori possano compilare ed eseguire correttamente il progetto. La disponibilità di opzioni specifiche per il progetto consente a molti sviluppatori di lavorare allo stesso documento senza compromettere la formattazione del file.

Per aprire le opzioni del progetto in Visual Studio per Mac, fare doppio clic sul nome del progetto oppure fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida, quindi scegliere **Opzioni**:

![Opzioni nel menu di scelta rapida](media/projects-and-solutions-image2.png)

Le opzioni modificabili includono quelle per compilare, eseguire e impostare il codice sorgente e il controllo della versione.

Le opzioni del progetto sono organizzate in cinque categorie diverse:

* **Generale** - In questa sezione è possibile impostare informazioni sul progetto, come nome, descrizione e spazio dei nomi predefinito, oltre al percorso del progetto.
* **Compilazione:** consente di impostare o modificare i profili pcl per le librerie di classi portabili. Consente anche di impostare opzioni del compilatore, configurazioni e comandi personalizzati. Qui è possibile impostare anche il percorso di output e il nome dell'assembly.
* **Esegui:** consente di creare configurazioni di esecuzione personalizzate in base al progetto.
* **Codice sorgente:** controlla la formattazione di molti tipi di file e convenzioni di denominazione diversi. In questa posizione è possibile anche impostare criteri di denominazione e stili di intestazione predefiniti.
* **Controllo della versione:** opzioni per impostare lo stile dei messaggi di commit quando si usa il controllo della versione con il progetto.

Ogni progetto può contenere opzioni specifiche del progetto, a seconda della piattaforma. Un progetto Xamarin.Android, come quello illustrato nell'immagine seguente, ad esempio, include opzioni relative alla compilazione Android (come le opzioni del linker) e all'applicazione (come le autorizzazioni):

![Opzioni di progetto Android](media/projects-and-solutions-image5.png)

Xamarin.iOS include opzioni correlate alla firma del bundle, ad esempio il profilo di provisioning da usare:

![Opzioni di progetto iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opzioni della soluzione

Le opzioni della soluzione sono come le opzioni del progetto, ma riguardano l'intera soluzione. Consentono di impostare le informazioni sull'autore, le impostazioni di compilazione, gli stili di formattazione del codice e il controllo della versione e permettono di assegnare il progetto di avvio nella soluzione.  È possibile accedere alla finestra di dialogo Opzioni soluzione dalla  voce di menu Opzioni soluzione **Project >,** dalla voce di menu di scelta rapida Opzioni nella soluzione nella finestra della soluzione o facendo doppio clic sulla soluzione nella finestra della soluzione:

![Opzioni della soluzione](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Vedi anche

* [Gestione delle proprietà di progetti e soluzioni (Visual Studio in Windows)](/visualstudio/ide/managing-project-and-solution-properties)