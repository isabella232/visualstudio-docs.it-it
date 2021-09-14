---
title: Azioni di compilazione
description: Questo articolo descrive le varie azioni di compilazione che possono essere usate per i progetti C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710483"
---
# <a name="build-actions"></a>Azioni di compilazione

Tutti i file di un progetto Visual Studio per Mac possiedono un'azione di compilazione, L'azione di compilazione controlla cosa accade al file durante una compilazione. 

>[!NOTE]
>Questo argomento si applica a Visual Studio per Mac. Per Visual Studio su Windows, vedere [Azioni di compilazione.](/visualstudio/ide/build-actions)

## <a name="set-a-build-action"></a>Impostare un'azione di compilazione

Per impostare un'azione di compilazione per un file in Visual Studio per Mac, è possibile fare clic con il pulsante destro del mouse su qualsiasi file e scegliere **Azione** di compilazione , come illustrato di seguito:

![Selezione dell'azione di compilazione da Esplora soluzioni](media/projects-and-solutions-image1.png)

Le azioni di compilazione per questo file verranno visualizzate nel menu a comparsa. 

## <a name="build-action-values"></a>Valori dell'azione di compilazione

Alcune delle azioni di compilazione comuni per i progetti che è possibile compilare in Visual Studio per Mac includono:

|Azione di compilazione | Tipi di progetto | Descrizione |
|--|--|--|
| **Compilazione** | any | Il file viene passato al compilatore C# come file di origine.|
| **Contenuto** | .NET, Xamarin | Per i progetti ASP.NET, questi file vengono inclusi come parte del sito quando questo viene distribuito. Per i progetti Xamarin.iOS e Xamarin.Mac, sono inclusi nel bundle dell'app.|
| **Embedded Resource** | .NET | Il file viene passato al compilatore C# come risorsa da incorporare nell'assembly. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), sarà quindi possibile usare lo spazio dei nomi `System.Reflection` per leggere il file dall'assembly.|
| **Nessuna** | any | Il file non fa parte della compilazione in alcun modo ed è incluso nel progetto per un facile accesso dall'IDE. Questo valore può essere usato per i file di documentazione come i file leggimi, ad esempio.|

> [!NOTE]
> È possibile definire azioni di compilazione aggiuntive per tipi di progetto specifici, pertanto l'elenco di azioni di compilazione dipende dal tipo di progetto e potrebbero venire visualizzati valori che non sono presenti in questo elenco.  

Per i progetti Xamarin.iOS esiste l'azione di compilazione **BundleResource**, che aggiunge il file al bundle dell'app. Per informazioni sulle azioni di compilazione specifiche per Xamarin.Android, vedere la guida al [processo di compilazione](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

È anche possibile selezionare più di un file in Esplora soluzioni, consentendo di impostare l'azione di compilazione su più file contemporaneamente.

## <a name="see-also"></a>Vedi anche

- [Azioni di compilazione (Visual Studio in Windows)](/visualstudio/ide/build-actions)