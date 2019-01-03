---
title: Avvisi di linee guida di base di C++
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.workload:
- cplusplus
ms.openlocfilehash: 59a26be52614baf5a8cca48f855f19432ff2af3b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926278"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usando i controlli delle linee guida di base di C++

Linee guida di base di C++ sono un set di linee guida, regole e le procedure consigliate sulla scrittura di codice in C++ creato da progettisti e gli esperti di C++ portabile. Visual Studio supporta attualmente un sottoinsieme di queste regole come parte dei relativi strumenti di analisi codice per C++. I controlli delle linee guida di base vengono installati per impostazione predefinita in Visual Studio 2017 e vengono [disponibile come pacchetto NuGet per Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Il progetto di linee guida di base di C++

Linee guida di base di C++ creato da Bjarne Stroustrup e così via, sono una Guida all'utilizzo di C++ moderno in modo sicuro ed efficace. Le linee guida enfatizzare l'indipendenza dai tipi statici e la sicurezza delle risorse. Le classi identificare modi per eliminare o ridurre al minimo le parti più soggette a errori del linguaggio e suggerire come rendere il codice più semplice e più efficiente in modo affidabile. Queste indicazioni vengono gestite dagli Standard C++ Foundation. Per altre informazioni, vedere la documentazione [linee guida di base di C++](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)e accedere ai file di progetto di linee guida di base di C++ documentazione sul [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Abilitare le linee guida C++ Core controllare nell'analisi del codice

È possibile abilitare analisi del codice sul progetto selezionando il **Abilita analisi codice su compilazione** casella di controllo la **analisi del codice** sezione del **pagine delle proprietà** finestra di dialogo per il progetto.

![Pagina delle proprietà per le impostazioni generali di analisi codice](../code-quality/media/cppcorecheck_codeanalysis_general.png)

Le regole C++ Core controllare sono le estensioni per il set di regole predefinite che vengono eseguiti quando è abilitata l'analisi del codice. Poiché le regole di controllo di base di C++ sono in fase di sviluppo, alcune regole sono ben definite e alcune potrebbero non essere pronto per l'uso in tutto il codice, ma possono risultare informativi. Le regole sono suddivise in due gruppi: è stato rilasciato e sperimentali. È possibile scegliere se eseguire le regole rilasciate o sperimentale nelle proprietà del progetto.

![Pagina delle proprietà per le impostazioni delle estensioni di analisi codice](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

Per abilitare o disabilitare i set di regole C++ Core verificare, aprire il **pagine delle proprietà** finestra di dialogo per il progetto. Sotto **le proprietà di configurazione**, espandere **analisi del codice**, **estensioni**. Nell'elenco a discesa accanto al controllo **Abilita C++ Core controllare (rilascio)** oppure **Abilita C++ Core controllare (sperimentale)**, scegliere **Sì** oppure **No**. Scegli **OK** oppure **applica** per salvare le modifiche.

## <a name="examples"></a>Esempi

Di seguito è riportato un esempio di alcuni dei problemi che è possono trovare le regole C++ Core controllare:

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

- C26494 è regola Type.5: Inizializzare sempre un oggetto.

- C26485 è regola Bounds.3: Decadimento non-matrice di puntatori.

- C26481 è regola Bounds.1: Non usare l'aritmetica dei puntatori. In alternativa, usare `span`.

Se gli oggetti ruleSet analisi di codice C++ Core controllare installati e abilitati quando si compila questo codice, i primi due avvisi vengono visualizzati, ma il terzo viene eliminato. Ecco l'output di compilazione dal codice di esempio:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Linee guida di base di C++ sono presenti che consentono di scrivere codice migliore e più sicuro. Tuttavia, se si dispone di un'istanza in cui non venga applicato una regola o un profilo, è facile eliminarlo direttamente nel codice. È possibile usare il `gsl::suppress` attributo per evitare che C++ Core controllare il rilevamento e creazione di report qualsiasi violazione di una regola in blocco di codice seguente. È possibile contrassegnare singole istruzioni per eliminare le regole specifiche. È anche possibile eliminare l'intero profilo limiti scrivendo `[[gsl::suppress(bounds)]]` senza includere un numero di regole specifici.

## <a name="supported-rule-sets"></a>Set di regole è supportata

Come vengono aggiunte nuove regole per il controllo di linee guida di base di C++, può aumentare il numero di avvisi generati per il codice preesistente. È possibile usare set di regole predefiniti per filtrare quali tipi di regole da abilitare. A partire da Visual Studio 2017 versione 15.3, il set di regole supportati sono:

  - **Le regole di puntatore Owner** imporre [controlla di gestione risorse correlati all'oggetto owner<T> linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Le regole di const** imporre [controlli correlati a const delle linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Le regole di puntatore non elaborato** imporre [di gestione risorse Controlla puntatori correlati a non elaborato linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Regole di puntatori univoci** imporre [controlli di gestione risorse correlati a tipi con semantica dei puntatori univoci delle linee guida di base C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Regole dei limiti** applicare le [delimita profilo delle linee guida di base di C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Regole di tipo** applicare le [tipo di profilo delle linee guida di base di C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).


È possibile scegliere di limitare gli avvisi solo da uno o più dei gruppi. Il **minimo Native** e **consigliato Native** regola set di includono le regole di controllo di base di C++ oltre a altri controlli di PREfast. Per visualizzare il disponibili set di regole, aprire la finestra di dialogo proprietà del progetto, selezionare **codice Analysis\General**, aprire l'elenco a discesa nel **set di regole** casella combinata e pick **Scegli più set di regole** . Per altre informazioni sull'uso di set di regole in Visual Studio, vedere [usando i set di regole per raggruppare regole di analisi codice](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Macro

Il controllo di linee guida di base di C++ viene fornito con un file di intestazione che definisce le macro che rendono più semplice eliminare le categorie di intere di avvisi nel codice:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Queste macro corrispondono ai set di regole ed espandono in un elenchi separati da spazi di numeri di avviso. Usando i costrutti pragma appropriate è possibile configurare il set di regole valido che è interessante per un progetto o una sezione di codice. Nell'esempio seguente, l'analisi del codice avviserà solo sui modificatori di costanti mancante:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attributi

Il compilatore Microsoft Visual C++ include un supporto limitato per la GSL Elimina attributo. Può essere utilizzato per non visualizzare avvisi su espressioni e istruzioni di blocco all'interno di una funzione.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>Eliminazione di analisi utilizzando le opzioni della riga di comando

Anziché #pragmas, è possibile usare opzioni della riga di comando nella pagina delle proprietà del file per non visualizzare avvisi per un progetto o un singolo file. Ad esempio, per disabilitare l'avviso 26400 per un file:

1. Il file in **Esplora soluzioni**

2. Scegliere **proprietà | C / C++ | Riga di comando**

3. Nel **opzioni aggiuntive** finestra Aggiungi `/wd26400`.

È possibile usare l'opzione della riga di comando per disabilitare temporaneamente tutte le analisi del codice per un file, specificando `/analyze-`. Questo genera l'avviso *D9025 override '/ANALYZE' con ' / analizzare-'*, che verrà visualizzato un promemoria di è possibile abilitare di nuovo l'analisi del codice in un secondo momento.

## <a name="corecheck_per_file"></a> Abilitare il controllo di linee guida di base di C++ nel file di progetto specifici

In alcuni casi può essere utile per analisi del codice di eseguire operazioni con stato attivato e comunque sfruttare l'IDE di Visual Studio. Di seguito è uno scenario di esempio che può essere usato per i progetti di grandi dimensioni per risparmiare tempo di compilazione e rendono più semplice per filtrare i risultati.

1.  Nella shell dei comandi impostare la `esp.extension` e `esp.annotationbuildlevel` variabili di ambiente.
2.  Avviare Visual Studio dalla shell dei comandi per ereditare tali variabili.
3.  Caricare il progetto e aprire le relative proprietà.
4.  Abilita analisi codice, selezionare i set di regole appropriate, ma non abilitare le estensioni di analisi codice.
5.  Passare al file di cui che si desidera analizzare con il controllo di linee guida di base di C++ e aprirne le relative proprietà.
6.  Scegli **C / C++ \Command opzioni della riga** e aggiungere `/analyze:plugin EspXEngine.dll`
7.  Disabilitare l'uso dell'intestazione precompilata (**C / C++ \Precompiled intestazioni**). Ciò è necessario perché il motore delle estensioni può tentare di leggere le informazioni interne da intestazione precompilata e se quest'ultimo è stato compilato con le opzioni di progetto predefinite, non saranno compatibile.
8.  Ricompilare il progetto. I controlli comuni di PREFast devono eseguire in tutti i file. Poiché il controllo di linee guida di base di C++ non è abilitato per impostazione predefinita, deve essere eseguita solo sul file di cui è configurato per usarlo.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Come usare il controllo di linee guida di base di C++ esternamente a Visual Studio
È possibile usare i controlli delle linee guida di base di C++ nelle compilazioni automatiche.

### <a name="msbuild"></a>MSBuild
 Il grafico di analisi del codice nativo (PREfast) è integrato nell'ambiente di MSBuild dai file di destinazioni personalizzate. È possibile per abilitarla, usare le proprietà del progetto e aggiungere il controllo di linee guida di base di C++ (che si basa su PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Assicurarsi di che aggiungere queste proprietà prima dell'importazione del file Microsoft.Cpp.targets. È possibile selezionare i set di regole specifici o creare un set di regole personalizzato o usare il set di regole predefinite che include altri controlli di PREfast.

È possibile eseguire il controllo di base di C++ solo nei file specificati utilizzando l'approccio descritto in [descritto in precedenza](#coreckeck_per_file), ma con i file di MSBuild. Le variabili di ambiente possono essere impostate utilizzando il `BuildMacro` elemento:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Se non si desidera modificare il file di progetto, è possibile passare le proprietà nella riga di comando:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Progetti non MSBuild
Se si usa un sistema di compilazione che non si basa su MSBuild è comunque possibile eseguire il controllo, ma è necessario acquisire familiarità con alcune caratteristiche interne di configurazione del motore di analisi del codice (che non è garantita a essere supportato in futuro).

È necessario impostare alcune variabili di ambiente e usare le opzioni della riga di comando appropriata per il compilatore. È preferibile usare l'ambiente di "strumenti prompt dei comandi nativi" in modo da non dover cercare percorsi specifici per il compilatore, includere le directory e così via.

1. **Variabili di ambiente**
   - `set esp.extensions=cppcorecheck.dll` Ciò indica al motore di caricare il modulo di linee guida di base di C++.
   - `set esp.annotationbuildlevel=ignore` In questo modo viene disabilitata per la logica che elabora le annotazioni SAL. Le annotazioni non influiscono sull'analisi del codice nel controllo di linee guida di base di C++, ma richiede loro elaborazione tempo (in alcuni casi molto tempo). Questa impostazione è facoltativa ma altamente consigliata.
   - `set caexcludepath=%include%` Si consiglia di disabilitare gli avvisi che vengono attivati in intestazioni standard. È possibile aggiungere più percorsi in questo caso, ad esempio il percorso per le intestazioni comuni nel progetto.
2. **Opzioni della riga di comando**
   - `/analyze`  Abilita l'analisi del codice (si consiglia di utilizzare anche /analyze: solo e /analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` Questa opzione Carica il motore delle estensioni di analisi codice di PREfast. Questo motore, a sua volta, carica il controllo di linee guida di base di C++.

## <a name="use-the-guideline-support-library"></a>Usare la libreria di supporto delle linee guida
 La libreria di supporto delle linee guida è progettata per aiutarti a seguire le linee guida di base. Il GSL include le definizioni che consentono di sostituire i costrutti soggetta a errori con alternative più sicure. Ad esempio, è possibile sostituire un `T*, length` coppia di parametri con il `span<T>` tipo. È disponibile all'indirizzo il GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). La libreria è open source, in modo che è possibile visualizzare le origini, commenti o contribuire. Il progetto è reperibile in [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a> Usare le linee guida C++ Core controllare nei progetti di Visual Studio 2015
  Se si usa Visual Studio 2015, il set di regole analisi codice C++ Core controllare non sono installati per impostazione predefinita. È necessario eseguire alcuni passaggi aggiuntivi prima di poter abilitare strumenti di analisi codice C++ Core verificare in Visual Studio 2015. Microsoft offre supporto per i progetti di Visual Studio 2015 con un pacchetto Nuget. Il pacchetto viene denominato Microsoft.CppCoreCheck ed è disponibile all'indirizzo [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Questo pacchetto è necessario almeno Visual Studio 2015 con Update 1 installato.

 Il pacchetto installa anche un altro pacchetto come dipendenza, una sola intestazione delle linee guida il supporto della libreria (GSL). È inoltre disponibile in GitHub all'indirizzo il GSL [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 A causa della modalità che vengono caricate le regole dell'analisi codice, è necessario installare il pacchetto Microsoft.CppCoreCheck NuGet in ogni progetto C++ che si desidera controllare all'interno di Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Per aggiungere il pacchetto Microsoft.CppCoreCheck al progetto in Visual Studio 2015

1. Nelle **Esplora soluzioni**, pulsante destro del mouse per aprire il menu di scelta rapida del progetto nella soluzione che si desidera aggiungere il pacchetto. Scegli **Gestisci pacchetti NuGet** per aprire il **Gestione pacchetti NuGet**.

2. Nel **Gestisci pacchetti NuGet** (finestra), cercare Microsoft.CppCoreCheck.

    ![Finestra Gestione pacchetti NuGet Mostra package CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Selezionare il pacchetto Microsoft.CppCoreCheck e quindi scegliere il **installare** pulsante per aggiungere le regole per il progetto.

   Il pacchetto NuGet aggiunge un file con estensione targets di MSBuild aggiuntivo al progetto che viene richiamato quando si abilita analisi codice sul progetto. Questo file con estensione targets aggiunge le regole di controllo di base di C++ come un'estensione aggiuntiva allo strumento di analisi del codice di Visual Studio. Quando viene installato il pacchetto, è possibile utilizzare la finestra di dialogo Pagine delle proprietà per abilitare o disabilitare le regole è state rilasciate e sperimentali.