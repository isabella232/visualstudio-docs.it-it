---
title: Risoluzione di assembly in fase di progettazione | Microsoft Docs
description: Informazioni su MSBuild risolvere i riferimenti agli assembly in fase di progettazione usando gli assembly di riferimento nel targeting pack.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 832448d53b7ae6841732bc27fe345c7d02b249c48d422859fc3642c086055f66
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369813"
---
# <a name="resolve-assemblies-at-design-time"></a>Risoluzione di assembly in fase di progettazione

Quando si aggiunge un riferimento a un assembly tramite la scheda **.NET** della finestra di dialogo **Aggiungi riferimento**, il riferimento punta a un riferimento assembly intermedio, vale a dire un assembly in cui sono contenute tutte le informazioni sul tipo e sulla firma, ma in cui non è incluso necessariamente del codice. Nella scheda **.NET** sono elencati gli assembly di riferimento corrispondenti agli assembly di runtime in .NET Framework. Sono elencati anche gli assembly di riferimento corrispondenti agli assembly di runtime nelle cartelle AssemblyFoldersEx registrate usate da terzi.

## <a name="multi-targeting"></a>Multitargeting

 Visual Studio consente di specificare come destinazione le versioni .NET Framework che vengono eseguite in più versioni del .NET Framework. Quando viene rilasciata una nuova versione .NET Framework, Il framework può essere installato usando un Targeting Pack e verrà automaticamente visualizzato come destinazione in Visual Studio.

## <a name="how-type-resolution-works"></a>Funzionamento della risoluzione dei tipi

 In fase di esecuzione, CLR risolve i tipi nell'assembly esaminando la GAC, la directory *bin* e tutti i percorsi di probe. Questa operazione è gestita dal caricatore Fusion. Tuttavia, come fa il caricatore Fusion a sapere cosa sta cercando? Ciò dipende da una risoluzione eseguita in fase di progettazione, quando l'applicazione viene compilata.

 Durante la compilazione, il compilatore risolve i tipi dell'applicazione mediante assembly di riferimento. Nel caso di .NET Framework versioni 2.0, 3.0 e 3.5, 4, 4.5 e 4.5.1, gli assembly di riferimento vengono installati contemporaneamente a .NET Framework.

 Gli assembly di riferimento sono forniti dal pacchetto di destinazione fornito con la versione corrispondente di .NET Framework SDK. Il framework in sé fornisce soltanto gli assembly di runtime. Per compilare le applicazioni, è necessario installare sia .NET Framework sia la versione corrispondente di .NET Framework SDK.

 Quando si sceglie come destinazione una versione di .NET Framework specifica, il sistema di compilazione risolve tutti i tipi usando gli assembly di riferimento contenuti nel Targeting Pack. In fase di esecuzione, il caricatore Fusion risolve questi stessi tipi negli assembly di runtime, che in genere si trovano nella GAC.

 Se gli assembly di riferimento non sono disponibili, il sistema di compilazione risolve i tipi degli assembly usando gli assembly di runtime. Poiché nella GAC gli assembly di runtime non sono distinti da numeri di versione secondaria, è possibile che la risoluzione venga eseguita nell'assembly errato. Questo può accadere, ad esempio, se si fa riferimento a un nuovo metodo introdotto in .NET Framework versione 3.5 ma si è impostata come destinazione la versione 3.0. La compilazione avrà esito positivo e l'applicazione verrà eseguita nel computer di compilazione. Avrà tuttavia esito negativo in caso di distribuzione in un computer in cui non è installata la versione 3.5.

 Il Targeting Pack fornito ora con .NET Framework SDK include un elenco di tutti gli assembly di runtime contenuti in quella versione del framework, definito elenco di ridistribuzione (redist), rendendo impossibile al sistema della compilazione di risolvere i tipi in una versione di assembly errata.

## <a name="see-also"></a>Vedi anche
- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
