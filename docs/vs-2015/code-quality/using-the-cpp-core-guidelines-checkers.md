---
title: Uso dei controlli Linee guida di base di C++ | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: fffa4cec6a2bd7a340b90776ac20dc486f28045b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173556"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Uso dei correttori Linee guida di base di C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I Linee guida di base di C++ sono un set di linee guida, regole e procedure consigliate per la scrittura di codice in C++ creati da esperti e designer C++.  Visual Studio ora supporta i pacchetti di componenti aggiuntivi che creano regole aggiuntive per gli strumenti di analisi del codice per verificare la conformità del codice alla Linee guida di base di C++ e suggerire miglioramenti.  
  
## <a name="the-c-core-guidelines-project"></a>Progetto Linee guida di base di C++  
 Creato da Bjarne Stroustrup e altri, il Linee guida di base di C++ è una guida all'uso di C++ moderno in modo sicuro ed efficace. Le linee guida enfatizzano l'indipendenza dai tipi statici e la sicurezza delle risorse. Identificano modi per eliminare o ridurre al minimo la maggior parte delle parti soggette a errori del linguaggio e suggerire come rendere il codice più semplice e più efficiente in modo affidabile. Queste linee guida sono gestite dalla base C++ standard. Per altre informazioni, vedere la documentazione [linee guida di base di C++](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e accedere ai file di progetto della documentazione di linee guida di base di C++ su [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft supporta il Linee guida di base di C++ sforzo rendendo Regole di base di C++ set di regole di analisi del codice che è possibile aggiungere ai progetti usando un pacchetto NuGet. Il pacchetto è denominato Microsoft. CppCoreCheck ed è disponibile all'indirizzo [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Per questo pacchetto è necessario avere almeno Visual Studio 2015 con Update 1 installato.  
  
 Il pacchetto installa anche un altro pacchetto come dipendenza, una libreria di supporto per le linee guida solo intestazione (GSL). GSL è disponibile anche in GitHub all'indirizzo [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Abilitare le linee guida Regole di base di C++ nell'analisi del codice  
 Per abilitare gli strumenti di analisi del codice Regole di base di C++, installare il pacchetto NuGet Microsoft. CppCoreCheck in ogni progetto C++ che si vuole controllare in Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Per aggiungere il pacchetto Microsoft. CppCoreCheck al progetto  
  
1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida del progetto nella soluzione a cui si desidera aggiungere il pacchetto. Scegliere **Gestisci pacchetti NuGet** per aprire **Gestione pacchetti NuGet**.  
  
2. Nella finestra **Gestione pacchetti NuGet** cercare Microsoft. CppCoreCheck.  
  
    ![Finestra di gestione pacchetti NuGet che mostra il pacchetto CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Selezionare il pacchetto Microsoft. CppCoreCheck, quindi scegliere il pulsante **Installa** per aggiungere le regole al progetto.  
  
   Il pacchetto NuGet aggiunge un file MSBuild. targets aggiuntivo al progetto che viene richiamato quando si Abilita l'analisi del codice nel progetto. Questo file con estensione targets aggiunge le regole di Regole di base di C++ come estensione aggiuntiva allo strumento di analisi del codice di Visual Studio.  
  
   È possibile abilitare l'analisi del codice nel progetto selezionando la casella di controllo **Abilita analisi codice su compilazione** nella sezione **analisi codice** della finestra di dialogo **pagine delle proprietà** del progetto.  
  
   ![Pagina delle proprietà per le impostazioni generali dell'analisi codice](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Le regole di Regole di base di C++ diventano parte dei set di regole predefiniti che vengono eseguiti quando è abilitata l'analisi del codice. Poiché le regole di Regole di base di C++ sono in fase di sviluppo, è possibile che alcune regole non siano pronte per l'uso in tutto il codice, ma possono essere informative durante lo sviluppo. Queste regole vengono rilasciate come sperimentali. È possibile scegliere se eseguire le regole rilasciate o sperimentali nelle proprietà del progetto.  
  
   ![Pagina delle proprietà per le impostazioni delle estensioni di analisi del codice](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Per abilitare o disabilitare i set di regole Regole di base di C++, aprire la finestra di dialogo **pagine delle proprietà** per il progetto. In **proprietà di configurazione**espandere  **analisi codice**, **estensioni**. Nel controllo a discesa accanto a **abilita regole di base di C++ (rilasciato)** o **Abilita regole di base di C++ (sperimentale)**, scegliere **Sì** o **No**. Scegliere **OK** o **applica** per salvare le modifiche.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Tipi di controllo, limiti e durate  
 Il pacchetto di Regole di base di C++ contiene attualmente i controlli per i profili indipendenza dai [tipi](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [sicurezza dei limiti](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)e [sicurezza della durata](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Di seguito è riportato un esempio del tipo di problemi che le regole di Regole di base di C++ possono trovare:  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 In questo esempio vengono illustrati alcuni avvisi che le regole di Regole di base di C++ possono trovare:  
  
- C26494 è il tipo di regola. 5: Inizializza sempre un oggetto.  
  
- C26485 è associato alle regole. 3: nessun decadimento da matrice a puntatore.  
  
- C26481 è associato alle regole. 1: non usare l'aritmetica dei puntatori. In alternativa, utilizzare `span`.  
  
  Se i set di regole di analisi del codice Regole di base di C++ sono installati e abilitati quando si compila questo codice, vengono restituiti i primi due avvisi, ma il terzo viene eliminato. Ecco l'output di compilazione del codice di esempio:  
  
**1>------compilazione avviata: progetto: CoreCheckExample, configurazione: debug Win32--**  
**----**  
**1> CoreCheckExample. cpp**  
**1> CoreCheckExample. vcxproj-> C:\utenti\nomeutente\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1> CoreCheckExample. vcxproj-> C:\utenti\nomeutente\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (PDB completo)**  
**c:\utenti\nomeutente\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): Warning C26494: la variabile ' arr ' è uninitializ**  
**ed. Inizializzare sempre un oggetto. (Type. 5: https: \/ /go.Microsoft.com/fwlink/p/?link**  
**ID = 620421)**  
**c:\utenti\nomeutente\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): Warning C26485: espressione ' arr ': nessuna matrice**  
**decadimento del puntatore. (limiti. 3: https: \/ /go.Microsoft.com/fwlink/p/?LinkId=620415)**  
**========== Compilazione: 1 completata, 0 non riuscita, 0 aggiornata, 0 ignorata ==========** 

I Linee guida di base di C++ sono utili per scrivere codice migliore e sicuro. Tuttavia, se si dispone di un'istanza in cui non è necessario applicare una regola o un profilo, è facile eliminarlo direttamente nel codice. È possibile utilizzare l' `gsl::suppress` attributo per impedire al regole di base di C++ di rilevare e segnalare eventuali violazioni di una regola nel blocco di codice seguente. È possibile contrassegnare singole istruzioni per l'eliminazione di regole specifiche. È anche possibile eliminare l'intero profilo dei limiti scrivendo `[[gsl::suppress(bounds)]]` senza includere un numero di regola specifico.  
  
## <a name="use-the-guideline-support-library"></a>Usare la libreria di supporto per le linee guida  
 Il pacchetto NuGet Microsoft. CppCoreCheck installa anche un pacchetto che contiene l'implementazione di Microsoft della libreria di supporto delle linee guida (GSL). GSL è disponibile anche in formato autonomo all'indirizzo [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . Questa libreria è utile se si desidera attenersi alle linee guida di base. Il GSL include definizioni che consentono di sostituire costrutti soggetti a errori con alternative più sicure. È ad esempio possibile sostituire una `T*, length` coppia di parametri con il `span<T>` tipo. Il GSL è open source, quindi se si vuole esaminare le origini, i commenti o i contributi di libreria, è possibile trovare il progetto in [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .
