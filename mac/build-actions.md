---
title: Azioni di compilazione
description: Questo articolo descrive le varie azioni di compilazione che possono essere usate per i progetti C#
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 6ef2cc3347480fceab23df12e53be65dd5432183
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224222"
---
# <a name="build-actions"></a>Azioni di compilazione

A tutti i file di un progetto Visual Studio per Mac è associata un'azione di compilazione che controlla cosa accade al file durante la compilazione. Per impostare questa azione, è possibile fare clic con il pulsante destro del mouse sul file e scegliere **Azione di compilazione**, come illustrato di seguito:

![Selezione dell'azione Compilazione da Esplora soluzioni](media/projects-and-solutions-image1.png)

Ecco alcune azioni di compilazione comuni per progetti C#:

* **Nessuna**: il file non fa parte della compilazione in alcun modo, è incluso nel progetto solo per facilitarne l'accesso dall'IDE.
* **Compilazione**: il file verrà passato al compilatore C# come file di origine.
* **EmbeddedResource**: il file verrà passato al compilatore C# come una risorsa da incorporare nell'assembly. Sarà quindi possibile usare lo spazio dei nomi `System.Reflection` per leggere il file dall'assembly.
* **Contenuto**: per i progetti ASP.NET, questi file vengono inclusi come parte del sito quando questo viene distribuito. Per i progetti Xamarin.iOS e Xamarin.Mac sono inclusi nel bundle dell'app.

È possibile selezionare più file in Esplora soluzioni. Ciò consente di impostare l'azione di compilazione per più file in una sola volta.

Sono anche disponibili azioni di compilazione per progetti specifici. Per i progetti Xamarin.iOS, ad esempio, esiste l'azione di compilazione **BundleResource**, che aggiunge il file al bundle dell'app. Per informazioni sulle azioni di compilazione specifiche per Xamarin.Android, vedere la guida al [processo di compilazione](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).