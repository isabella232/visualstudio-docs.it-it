---
title: Usando i controlli delle linee guida di base di C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1153f7a32c26946fafb1230699c4afcae976cd9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799561"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usando i controlli delle linee guida di base di C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Linee guida di base di C++ sono un set di linee guida, regole e le procedure consigliate sulla scrittura di codice in C++ creato da progettisti e gli esperti di C++ portabile.  Visual Studio supporta ora i componenti dei pacchetti che creano le regole aggiuntive per il codice di strumenti di analisi per verificare il codice per la conformità con le linee guida di base C++ e suggerire miglioramenti.  
  
## <a name="the-c-core-guidelines-project"></a>Il progetto di linee guida di base di C++  
 Linee guida di base di C++ creato da Bjarne Stroustrup e così via, sono una Guida all'utilizzo di C++ moderno in modo sicuro ed efficace. Le linee guida enfatizzare l'indipendenza dai tipi statici e la sicurezza delle risorse. Le classi identificare modi per eliminare o ridurre al minimo le parti più soggette a errori del linguaggio e suggerire come rendere il codice più semplice e più efficiente in modo affidabile. Queste indicazioni vengono gestite dagli Standard C++ Foundation. Per altre informazioni, vedere la documentazione [linee guida di base di C++](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e accedere ai file di progetto di linee guida di base di C++ documentazione sul [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft supporta lo sforzo di linee guida di base di C++, rendendo C++ Core controlla i set di regole di analisi di codice che è possibile aggiungere ai progetti usando un pacchetto Nuget. Il pacchetto viene denominato Microsoft.CppCoreCheck ed è disponibile all'indirizzo [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Questo pacchetto è necessario almeno Visual Studio 2015 con Update 1 installato.  
  
 Il pacchetto installa anche un altro pacchetto come dipendenza, una sola intestazione delle linee guida il supporto della libreria (GSL). È inoltre disponibile in GitHub all'indirizzo il GSL [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Abilitare le linee guida C++ Core controllare nell'analisi del codice  
 Per abilitare gli strumenti di analisi di codice C++ Core controllare, installare il pacchetto Microsoft.CppCoreCheck NuGet in ogni progetto C++ che si desidera controllare all'interno di Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Per aggiungere il pacchetto Microsoft.CppCoreCheck al progetto  
  
1. Nelle **Esplora soluzioni**, pulsante destro del mouse per aprire il menu di scelta rapida del progetto nella soluzione che si desidera aggiungere il pacchetto. Scegli **Gestisci pacchetti NuGet** per aprire il **Gestione pacchetti NuGet**.  
  
2. Nel **Gestisci pacchetti NuGet** (finestra), cercare Microsoft.CppCoreCheck.  
  
    ![Finestra Gestione pacchetti NuGet Mostra package CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Selezionare il pacchetto Microsoft.CppCoreCheck e quindi scegliere il **installare** pulsante per aggiungere le regole per il progetto.  
  
   Il pacchetto NuGet aggiunge un file con estensione targets di MSBuild aggiuntivo al progetto che viene richiamato quando si abilita analisi codice sul progetto. Questo file con estensione targets aggiunge le regole di controllo di base di C++ come un'estensione aggiuntiva allo strumento di analisi del codice di Visual Studio.  
  
   È possibile abilitare analisi del codice sul progetto selezionando il **Abilita analisi codice su compilazione** casella di controllo la **analisi del codice** sezione del **pagine delle proprietà** finestra di dialogo per il progetto.  
  
   ![Pagina delle proprietà per le impostazioni generali di analisi codice](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Le regole C++ Core controllare diventano parte del set di regole predefinite che vengono eseguiti quando è abilitata l'analisi del codice. Poiché le regole di controllo di base di C++ sono in fase di sviluppo, alcune regole potrebbero non essere pronti per l'uso in tutto il codice, ma possono risultare informativi durante lo sviluppo. Queste regole vengono rilasciate come sperimentale. È possibile scegliere se eseguire le regole rilasciate o sperimentale nelle proprietà del progetto.  
  
   ![Pagina delle proprietà per le impostazioni delle estensioni di analisi codice](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Per abilitare o disabilitare i set di regole C++ Core verificare, aprire il **pagine delle proprietà** finestra di dialogo per il progetto. Sotto **le proprietà di configurazione**, espandere **analisi del codice**, **estensioni**. Nell'elenco a discesa accanto al controllo **Abilita C++ Core controllare (rilascio)** oppure **Abilita C++ Core controllare (sperimentale)**, scegliere **Sì** oppure **No**. Scegli **OK** oppure **applica** per salvare le modifiche.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Controllare i tipi, dei limiti e durate  
 Il pacchetto C++ Core controllare attualmente contiene controlli per la [indipendenza dai tipi](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [delimita safety](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), e [safety durata](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) profili.  
  
 Di seguito è riportato un esempio del tipo di problemi che è possono trovare le regole di controllo di base di C++:  
  
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
  
 Questo esempio illustra alcuni degli avvisi che è possono trovare le regole C++ Core controllare:  
  
- C26494 è regola Type.5: inizializzare sempre un oggetto.  
  
- C26485 è regola Bounds.3: decay non-matrice di puntatori.  
  
- C26481 è regola Bounds.1: non usare l'aritmetica dei puntatori. In alternativa, usare `span`.  
  
  Se gli oggetti ruleSet analisi di codice C++ Core controllare installati e abilitati quando si compila questo codice, i primi due avvisi vengono visualizzati, ma il terzo viene eliminato. Ecco l'output di compilazione dal codice di esempio:  
  
  **1 >---compilazione avviata: progetto: CoreCheckExample, configurazione: Debug Win32:**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (PDB completo)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): avviso C26494: la variabile 'arr' è uninitializ**  
**ed. inizializzare sempre un oggetto. (type.5: http://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): avviso C26485: espressione 'arr': non matrice da**  
 **decay puntatore. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**=== Compilazione: 1 completata, 0 non riuscite, 0 aggiornata, 0 ignorate ===** esistono linee guida di base di C++ che consentono di scrivere codice migliore e più sicuro. Tuttavia, se si dispone di un'istanza in cui non venga applicato una regola o un profilo, è facile eliminarlo direttamente nel codice. È possibile usare il `gsl::suppress` attributo per evitare che C++ Core controllare il rilevamento e creazione di report qualsiasi violazione di una regola in blocco di codice seguente. È possibile contrassegnare singole istruzioni per eliminare le regole specifiche. È anche possibile eliminare l'intero profilo limiti scrivendo `[[gsl::suppress(bounds)]]` senza includere un numero di regole specifici.  
  
## <a name="use-the-guideline-support-library"></a>Usare la libreria di supporto delle linee guida  
 Il pacchetto Microsoft.CppCoreCheck NuGet installa anche un pacchetto che contiene l'implementazione Microsoft della libreria di supporto delle linee guida (GSL). Il GSL è anche disponibile in forma autonoma al [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Questa libreria è utile se si vuole seguire le linee guida di base. Il GSL include le definizioni che consentono di sostituire i costrutti soggetta a errori con alternative più sicure. Ad esempio, è possibile sostituire un `T*, length` coppia di parametri con il `span<T>` tipo. Il GSL è open source, pertanto se si desidera esaminare le origini di libreria, come commento o contribuire, il progetto è reperibile in [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).



