---
title: 'Procedura dettagliata: uso delle API del profiler | Microsoft Docs'
description: Informazioni su come usare le API del profiler per limitare la quantità di dati raccolti durante la profilatura della strumentazione.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac6bb36fd6b29ce94c79e9e173c00257473c6ab2449592ae658eda47153d256c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121354040"
---
# <a name="walkthrough-using-profiler-apis"></a>Procedura dettagliata: Uso delle API del profiler

Nella procedura dettagliata viene usata un'applicazione C# per illustrare l'uso delle API di Strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le API del profiler consentono di limitare la quantità di dati raccolti durante la profilatura della strumentazione.

 In genere i passaggi descritti in questa procedura dettagliata si applicano a un'applicazione C/C++. Per ogni linguaggio, è necessario configurare l'ambiente di compilazione in modo appropriato.

 Si inizia generalmente usando la profilatura campione per analizzare le prestazioni dell'applicazione. Se la profilatura campione non restituisce informazioni che indicano un collo di bottiglia, è possibile che la profilatura della strumentazione offra un livello di dettaglio maggiore. La profilatura della strumentazione è molto utile per esaminare l'interazione tra thread.

 Per un livello di dettaglio maggiore è tuttavia necessario raccogliere più dati. È possibile quindi che la profilatura della strumentazione crei file di dati di grandi dimensioni. È anche possibile che la strumentazione comprometta le prestazioni dell'applicazione. Per altre informazioni, vedere [Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md) e [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)

 Il profiler di Visual Studio consente di limitare la raccolta dei dati. Questa procedura dettagliata offre un esempio su come limitare la raccolta dei dati usando le API del profiler. Il profiler di Visual Studio offre un'API per il controllo della raccolta dei dati all'interno di un'applicazione.

 ::: moniker range="vs-2017"
 Per il codice nativo, le API del profiler di Visual Studio si trovano in *VSPerf.dll*. Il file di intestazione *VSPerf.h* e la libreria di importazione *VSPerf.lib* si trovano nella directory *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*.  Per le app a 64 bit, la cartella è *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*
 ::: moniker-end

 Per il codice gestito, le API del profiler siMicrosoft.VisualStudio.Profiler.dll *.* Questa DLL è disponibile nella directory *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*. Per le app a 64 bit, la cartella è *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*. Per altre informazioni, vedere [Profiler](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Prerequisiti
 Questa procedura dettagliata presuppone che l'ambiente di sviluppo scelto sia configurato per supportare il debug e il campionamento. Gli argomenti seguenti offrono una panoramica di questi prerequisiti:

- [Procedura: Scegliere i metodi di raccolta](../profiling/how-to-choose-collection-methods.md)

- [Procedura: Fare riferimento alle Windows simboli](../profiling/how-to-reference-windows-symbol-information.md)

 Per impostazione predefinita, quando viene avviato, il profiler raccoglie i dati a livello globale. Il codice seguente all'inizio del programma disabilita la profilatura globale.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 È possibile disabilitare la raccolta dei dati nella riga di comando senza usare una chiamata API. Questa procedura presuppone che l'ambiente di compilazione avviata tramite riga di comando sia configurato per eseguire gli strumenti di profilatura e come strumenti di sviluppo. Include le impostazioni necessarie per VSInstr e VSPerfCmd. Vedere [Strumenti di profilatura della riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md).

## <a name="limit-data-collection-using-profiler-apis"></a>Limitare la raccolta dei dati usando le API del profiler

#### <a name="to-create-the-code-to-profile"></a>Per creare il codice per il profilo

1. Creare un nuovo progetto C# in Visual Studio o usare una compilazione avviata tramite riga di comando, a seconda delle preferenze.

    > [!NOTE]
    > La compilazione deve fare riferimento alla libreria *Microsoft.VisualStudio.Profiler.dll* che si trova nella directory *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*.

2. Copiare il codice riportato di seguito e incollarlo nel progetto:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using Microsoft.VisualStudio.Profiler;

    namespace ConsoleApplication1
    {
        class Program
        {
            public class A
            {
                private int _x;

                public A(int x)
                {
                    _x = x;
                }

                public int DoNotProfileThis()
                {
                    return _x * _x;
                }

                public int OnlyProfileThis()
                {
                    return _x + _x;
                }

                public static void Main()
                {
                    DataCollection.StopProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    A a = new A(2);
                    Console.WriteLine("2 square is {0}", a.DoNotProfileThis());

                    DataCollection.StartProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    int x;
                    x = a.OnlyProfileThis();

                    DataCollection.StopProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    Console.WriteLine("2 doubled is {0}", x);
                }
            }

        }
    }
    ```

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Per raccogliere e visualizzare i dati nell'IDE di Visual Studio

1. Aprire l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Scegliere **Profiler** dal menu **Analizza** e quindi **selezionare Nuova sessione di prestazioni.**

2. Aggiungere il file binario compilato per l'elenco **Destinazioni** nella finestra **Esplora prestazioni**. Fare clic con il pulsante destro del mouse su **Destinazioni** e selezionare **Aggiungi binario di destinazione**. Nella finestra di dialogo **Aggiungi binario di destinazione** selezionare il file binario e fare clic su **Apri**.

3. Nell'elenco **Metodo** della barra degli strumenti **Esplora prestazioni** fare clic su **Strumentazione**.

4. Fare clic su **Avvio con analisi**.

    Il profiler instrumenterà ed eseguirà il file binario e creerà un file del report di prestazioni. Il file del report di prestazioni verrà visualizzato nel nodo **Report** di **Esplora prestazioni**.

5. Aprire il file del report di prestazioni ottenuto.

   Per impostazione predefinita, quando viene avviato, il profiler raccoglie i dati a livello globale. Il codice seguente all'inizio del programma disabilita la profilatura globale.

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Per raccogliere e visualizzare i dati nella riga di comando

1. Compilare una versione di debug del codice di esempio creato nella procedura dettagliata illustrata in precedenza per la creazione di codice per il profilo.

2. Per profilare un'applicazione gestita, digitare il comando seguente e impostare le variabili di ambiente appropriate:

     **VsPerfCLREnv /traceon**

3. Digitare il comando seguente: **VSInstr \<filename>.exe**

4. Digitare il comando seguente: **VSPerfCmd /start:trace /output: \<filename> vsp**

5. Digitare il comando seguente: **VSPerfCmd /globaloff**

6. Uscire dal programma.

7. Digitare il comando seguente: **VSPerfCmd /shutdown**

8. Digitare il comando seguente: **VSPerfReport /calltrace: \<filename> .vsp**

     Viene creato un file con estensione *csv* nella directory corrente con i dati sulle prestazioni risultanti.

## <a name="see-also"></a>Vedi anche

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Visual Studio riferimento all'API del profiler (nativo)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Introduzione](../profiling/getting-started-with-performance-tools.md)
- [Usare gli strumenti per la profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
