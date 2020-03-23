---
title: Risoluzione di assembly in fase di progettazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69f5ba2627e2d659665fa0bd3fbf706f9cad5573
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632563"
---
# <a name="resolve-assemblies-at-design-time"></a>Risoluzione di assembly in fase di progettazione

Quando si aggiunge un riferimento a un assembly tramite la scheda **.NET** della finestra di dialogo **Aggiungi riferimento**, il riferimento punta a un riferimento assembly intermedio, vale a dire un assembly in cui sono contenute tutte le informazioni sul tipo e sulla firma, ma in cui non è incluso necessariamente del codice. Nella scheda **.NET** sono elencati gli assembly di riferimento corrispondenti agli assembly di runtime in .NET Framework. Sono elencati anche gli assembly di riferimento corrispondenti agli assembly di runtime nelle cartelle AssemblyFoldersEx registrate usate da terzi.

## <a name="multi-targeting"></a>Multitargeting

 Visual Studio consente di indirizzare le versioni di .NET Framework eseguite in più versioni di .NET Framework. Quando viene rilasciata una nuova versione di .NET Framework, Framework può essere installato utilizzando un pacchetto di destinazione e verrà visualizzato automaticamente come destinazione in Visual Studio.

## <a name="how-type-resolution-works"></a>Funzionamento della risoluzione dei tipi

 In fase di esecuzione, CLR risolve i tipi nell'assembly esaminando la Global Assembly Cache, la directory *bin* e gli eventuali percorsi di sondaggio. Questa operazione è gestita dal caricatore Fusion. Tuttavia, come fa il caricatore Fusion a sapere cosa sta cercando? Ciò dipende da una risoluzione eseguita in fase di progettazione, quando l'applicazione viene compilata.

 Durante la compilazione, il compilatore risolve i tipi dell'applicazione mediante assembly di riferimento. Nel caso di .NET Framework versioni 2.0, 3.0 e 3.5, 4, 4.5 e 4.5.1, gli assembly di riferimento vengono installati contemporaneamente a .NET Framework.

 Gli assembly di riferimento sono forniti dal pacchetto di destinazione fornito con la versione corrispondente di .NET Framework SDK. Il framework in sé fornisce soltanto gli assembly di runtime. Per compilare le applicazioni, è necessario installare sia .NET Framework sia la versione corrispondente di .NET Framework SDK.

 Quando si sceglie come destinazione una versione di .NET Framework specifica, il sistema di compilazione risolve tutti i tipi usando gli assembly di riferimento contenuti nel Targeting Pack. In fase di esecuzione, il caricatore di fusione risolve questi stessi tipi negli assembly di runtime, che in genere si trovano nella Global Assembly Cache.

 Se gli assembly di riferimento non sono disponibili, il sistema di compilazione risolve i tipi degli assembly usando gli assembly di runtime. Poiché nella GAC gli assembly di runtime non sono distinti da numeri di versione secondaria, è possibile che la risoluzione venga eseguita nell'assembly errato. Questo può accadere, ad esempio, se si fa riferimento a un nuovo metodo introdotto in .NET Framework versione 3.5 ma si è impostata come destinazione la versione 3.0. La compilazione avrà esito positivo e l'applicazione verrà eseguita nel computer di compilazione. Avrà tuttavia esito negativo in caso di distribuzione in un computer in cui non è installata la versione 3.5.

 Il Targeting Pack fornito ora con .NET Framework SDK include un elenco di tutti gli assembly di runtime contenuti in quella versione del framework, definito elenco di ridistribuzione (redist), rendendo impossibile al sistema della compilazione di risolvere i tipi in una versione di assembly errata.

## <a name="see-also"></a>Vedere anche
- [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
