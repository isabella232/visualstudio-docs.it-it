---
title: Uso dei C++ controlli delle linee guida di base | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 946b46bfb5101154832e10b61cd861b0c104dc14
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275292"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Uso dei correttori Linee guida di base di C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le C++ linee guida di base sono un set portatile di linee guida, regole e procedure consigliate C++ per la C++ scrittura di codice in creato da esperti e designer.  Visual Studio ora supporta i pacchetti di componenti aggiuntivi che creano regole aggiuntive per gli strumenti di analisi del codice per verificare la conformità del C++ codice con le linee guida di base e suggerire miglioramenti.  
  
## <a name="the-c-core-guidelines-project"></a>Progetto C++ di linee guida principali  
 Creato da Bjarne Stroustrup e altre, le C++ linee guida principali sono una guida all'uso C++ moderno in modo sicuro ed efficace. Le linee guida enfatizzano l'indipendenza dai tipi statici e la sicurezza delle risorse. Identificano modi per eliminare o ridurre al minimo la maggior parte delle parti soggette a errori del linguaggio e suggerire come rendere il codice più semplice e più efficiente in modo affidabile. Queste linee guida sono gestite dalla base C++ standard. Per altre informazioni, vedere la documentazione, [ C++ le linee guida di base](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e C++ accedere ai file di progetto della documentazione delle linee guida di base su [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft supporta le C++ linee guida di base per C++ il controllo dei set di regole di analisi del codice principali che è possibile aggiungere ai progetti usando un pacchetto NuGet. Il pacchetto è denominato Microsoft. CppCoreCheck ed è disponibile in [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Per questo pacchetto è necessario avere almeno Visual Studio 2015 con Update 1 installato.  
  
 Il pacchetto installa anche un altro pacchetto come dipendenza, una libreria di supporto per le linee guida solo intestazione (GSL). GSL è disponibile anche in GitHub all' [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Abilitare le C++ linee guida per il controllo principale nell'analisi del codice  
 Per abilitare gli C++ strumenti di analisi del codice per la verifica principale, installare il pacchetto NuGet Microsoft C++ . CppCoreCheck in ogni progetto che si vuole controllare in Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Per aggiungere il pacchetto Microsoft. CppCoreCheck al progetto  
  
1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida del progetto nella soluzione a cui si desidera aggiungere il pacchetto. Scegliere **Gestisci pacchetti NuGet** per aprire **Gestione pacchetti NuGet**.  
  
2. Nella finestra **Gestione pacchetti NuGet** cercare Microsoft. CppCoreCheck.  
  
    ![Finestra di gestione pacchetti NuGet che mostra il pacchetto CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Selezionare il pacchetto Microsoft. CppCoreCheck, quindi scegliere il pulsante **Installa** per aggiungere le regole al progetto.  
  
   Il pacchetto NuGet aggiunge un file MSBuild. targets aggiuntivo al progetto che viene richiamato quando si Abilita l'analisi del codice nel progetto. Questo file con estensione targets C++ aggiunge le regole di controllo di base come estensione aggiuntiva allo strumento di analisi del codice di Visual Studio.  
  
   È possibile abilitare l'analisi del codice nel progetto selezionando la casella di controllo **Abilita analisi codice su compilazione** nella sezione **analisi codice** della finestra di dialogo **pagine delle proprietà** del progetto.  
  
   ![Pagina delle proprietà per le impostazioni generali dell'analisi codice](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Le C++ regole di base del controllo diventano parte dei set di regole predefiniti che vengono eseguiti quando è abilitata l'analisi del codice. Poiché le C++ regole di base del controllo sono in fase di sviluppo, alcune regole potrebbero non essere pronte per l'uso in tutto il codice, ma possono essere informative durante lo sviluppo. Queste regole vengono rilasciate come sperimentali. È possibile scegliere se eseguire le regole rilasciate o sperimentali nelle proprietà del progetto.  
  
   ![Pagina delle proprietà per le impostazioni delle estensioni di analisi del codice](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Per abilitare o disabilitare i C++ set di regole di base di controllo, aprire la finestra di dialogo **pagine delle proprietà** per il progetto. In **proprietà di configurazione**espandere **analisi codice**, **estensioni**. Nel controllo a discesa accanto a **Abilita C++ controllo principale (rilasciato)** o **Abilita C++ controllo principale (sperimentale)** , scegliere **Sì** o **No**. Scegliere **OK** o **applica** per salvare le modifiche.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Tipi di controllo, limiti e durate  
 Il C++ pacchetto di verifica principale contiene attualmente i controlli per i profili indipendenza dai [tipi](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [sicurezza dei limiti](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)e [sicurezza della durata](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Di seguito è riportato un esempio del tipo di problemi che C++ le regole di controllo principali possono trovare:  
  
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
  
 Questo esempio illustra alcuni degli avvisi che possono essere trovati C++ dalle regole di controllo principali:  
  
- C26494 è il tipo di regola. 5: Inizializza sempre un oggetto.  
  
- C26485 è associato alle regole. 3: nessun decadimento da matrice a puntatore.  
  
- C26481 è associato alle regole. 1: non usare l'aritmetica dei puntatori. In alternativa, utilizzare `span`.  
  
  Se i C++ set di regole di analisi del codice di base del controllo vengono installati e abilitati quando si compila il codice, i primi due avvisi vengono restituiti, ma il terzo viene eliminato. Ecco l'output di compilazione del codice di esempio:  
  
**1 >------compilazione avviata: progetto: CoreCheckExample, configurazione: debug Win32--**  
**----**  
**1 > CoreCheckExample. cpp**  
**1 > CoreCheckExample. vcxproj-> C:\utenti\nomeutente\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample. vcxproj-> C:\utenti\nomeutente\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (PDB completo)**  
**c:\utenti\nomeutente\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): Warning C26494: la variabile ' arr ' è uninitializ**  
**ed. inizializzare sempre un oggetto. (Type. 5: https://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\utenti\nomeutente\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): Warning C26485: espressione ' arr ': nessuna matrice**  
**decadimento del puntatore. (limiti. 3: https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = = **Compilazione: 1 completata, 0 non riuscite, 0 aggiornata, 0 ignorate = =** = = = = = = = = Le C++ linee guida di base sono disponibili per semplificare la scrittura di codice migliore e sicuro. Tuttavia, se si dispone di un'istanza in cui non è necessario applicare una regola o un profilo, è facile eliminarlo direttamente nel codice. È possibile usare l'attributo `gsl::suppress` per impedire C++ al controllo principale di rilevare e segnalare eventuali violazioni di una regola nel blocco di codice seguente. È possibile contrassegnare singole istruzioni per l'eliminazione di regole specifiche. È anche possibile eliminare l'intero profilo dei limiti scrivendo `[[gsl::suppress(bounds)]]` senza includere un numero di regola specifico.  
  
## <a name="use-the-guideline-support-library"></a>Usare la libreria di supporto per le linee guida  
 Il pacchetto NuGet Microsoft. CppCoreCheck installa anche un pacchetto che contiene l'implementazione di Microsoft della libreria di supporto delle linee guida (GSL). GSL è disponibile anche in formato autonomo in [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). Questa libreria è utile se si desidera attenersi alle linee guida di base. Il GSL include definizioni che consentono di sostituire costrutti soggetti a errori con alternative più sicure. È ad esempio possibile sostituire un `T*, length` coppia di parametri con il tipo di `span<T>`. Il GSL è open source, quindi se si vuole esaminare le origini, i commenti o i contributi di libreria, il progetto è disponibile in [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).
