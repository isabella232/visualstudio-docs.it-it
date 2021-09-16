---
title: Modifiche al codice supportate (C++) | Microsoft Docs
description: Informazioni su quali modifiche al codice sono supportate quando si usa la funzionalità Modifica e continuazione durante il debug di un progetto C++ in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: f1a49c46c975d37f2b0b43531029b0ae5a28d4f8
ms.sourcegitcommit: 811e4ee80311433fefbe6d6223bf72c431008403
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2021
ms.locfileid: "127890468"
---
# <a name="supported-code-changes-c"></a>Modifiche al codice supportate (C++)
Modifica e continuazione per i progetti C++ gestisce la maggior parte dei tipi di modifiche al codice. Alcune modifiche non possono tuttavia essere applicate durante l'esecuzione del programma. Per applicare tali modifiche, è necessario arrestare l'esecuzione e compilare una versione aggiornata del codice.

 Vedere [Modifica e continuazione (C++)](../debugger/edit-and-continue-visual-cpp.md) per informazioni sull'uso di Modifica e continuazione per C++ in Visual Studio.

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Requisiti
### <a name="build-settings-project--properties"></a>Impostazioni di compilazione (Project > proprietà):
  1. **C/C++ > generale > informazioni** di debug : Database di programma per Modifica e continuazione ( `/ZI` )
  2. **Generazione di codice C/C++ > e > ricompilazione minima:** Sì ( `/Gm` )
  3. **Il linker > generale > il collegamento incrementale:** Sì ( `/INCREMENTAL` )

     Eventuali impostazioni del linker incompatibili ( ad esempio , o ...) devono `/SAFESEH` generare `/OPT:` l'avviso _LNK4075 durante_ la compilazione.  
     Esempio: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Impostazioni del debugger (Opzioni > debug > Generale):
  - Abilita Modifica e continuazione nativo

     Eventuali impostazioni del compilatore o del linker incompatibili causano un errore durante Modifica e continuazione.  
     Esempio: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Modifiche non supportate
 Le modifiche C/C++ seguenti non possono essere applicate durante una sessione di debug. Se si apporta una di queste modifiche e quindi si tenta di applicare le modifiche al codice, viene visualizzato un messaggio di errore o di avviso nella **finestra Output.**

- La maggior parte delle modifiche a dati globali o statici.

- Le modifiche a file eseguibili copiati da un altro computer e non compilati localmente.

- Le modifiche a un tipo di dati che hanno effetto sul layout di un oggetto, ad esempio i membri dati di una classe.

- Aggiunta di più di 64 KB di nuovo codice o nuovi dati.

- Aggiunta di variabili che richiedono un costruttore in un punto precedente al puntatore all'istruzione.

- Modifiche che interessano il codice per il quale è necessaria l'inizializzazione di runtime.

- Aggiunta di gestori di eccezioni, in alcune istanze.

- Modifiche di file di risorse.

- Modifiche del codice di file di sola lettura.

- Modifiche del codice privo di un file PDB corrispondente.

- Modifiche del codice privo di un file oggetto.

* Modifica delle espressioni lambda che:
  - Avere un membro statico o globale.
  - Vengono passati a std::function. Ciò causa una violazione ODR autentica e genera l'errore C1092.

- Le librerie statiche non vengono aggiornate con la funzionalità Modifica e continuazione. Se si apporta una modifica in una libreria statica, l'esecuzione continua con la versione precedente e non viene visualizzato alcun avviso.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Scenari non supportati
 Modifica e continuazione per C/C++ non è disponibile nei seguenti scenari di debug:

- Debug di applicazioni native compilate con [/Zo (Ottimizzare il debug)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Nelle versioni di Visual Studio precedenti a Visual Studio 2015 Update 1, debug di app o componenti UWP. A partire da Visual Studio 2015 Update 1, è possibile usare Modifica e continuazione nelle app C++ UWP e nelle app DirectX, perché ora supporta l'opzione del compilatore con l'opzione `/ZI` `/bigobj` . È anche possibile usare Modifica e continuazione con file binari compilati con l'opzione `/FASTLINK` .

- Debug delle app dello Store 8/8.1. Questi progetti usano il set di strumenti VC 120 e l'opzione `/bigobj` C/C++. Modifica e continuazione con è supportato solo nel set di strumenti `/bigobj` di VC 140.

- Debug in Windows 98.

- Debug in modalità mista (nativo/gestito).

- Debug JavaScript.

- Debug SQL.

- Debug di un file dump.

- Modifica di codice dopo un'eccezione non gestita, quando l'opzione **Rimuovi stack di chiamate su eccezioni non gestite** non è selezionata.

- Debug di un'app usando **Connetti a** invece di eseguire l'app da **Start** nel menu **Debug** .

- Debug di codice ottimizzato.

- Debug di una versione precedente del codice dopo l'esito negativo della compilazione di una nuova versione a causa di errori di compilazione.

- Uso di un percorso del *compilatore personalizzato (cl.exe*). Per motivi di sicurezza, per la ricompilazione di un file durante Modifica e continuazione, Visual Studio usa sempre il compilatore installato. Se si usa un percorso del compilatore personalizzato, ad esempio tramite una variabile personalizzata nel file, viene visualizzato un avviso e Visual Studio usa il compilatore installato della stessa `$(ExecutablePath)` `*.props` versione/architettura.

- Sistema di compilazione FASTBuild. FASTBuild non è attualmente compatibile con l'opzione del compilatore "Abilita ricompilazione minima ( )" e pertanto Modifica e `/Gm` continuazione non è supportato.

- Architetture legacy/set di strumenti vc. Con il set di strumenti VC 140, il debugger predefinito supporta Modifica e continuazione con le applicazioni X86 e X64. I set di strumenti legacy supportano solo le applicazioni X86. I set di strumenti precedenti a VC 120 devono usare il debugger legacy selezionando "Opzioni _di debug > > Generale >_ Usa modalità di compatibilità nativa" per usare Modifica e continuazione.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Limitazioni di collegamento

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opzioni dei linker che disabilitano Modifica e continuazione
 La funzionalità Modifica e continuazione viene disabilitata dalle seguenti opzioni dei linker:

- L'impostazione di **/OPT:REF**, **/OPT:ICF** o **/INCREMENTAL:NO** provoca la disattivazione di Modifica e continuazione con la visualizzazione del seguente messaggio di avviso:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- **L'impostazione di /ORDER**, **/RELEASE** o **/FORCE** disabilita Modifica e continuazione con l'avviso seguente:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- L'impostazione di qualsiasi opzione che impedisce la creazione di un file di database di programma con estensione pdb provoca la disattivazione di Modifica e continuazione senza la visualizzazione di un messaggio di avviso specifico.

### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Limitazioni di ricollegamento automatico
 Per impostazione predefinita, il programma viene ricollegato automaticamente al termine di una sessione di debug in modalità Modifica e continuazione per creare un eseguibile aggiornato.

 Se il debug viene effettuato da una posizione diversa dal percorso di compilazione originale, non sarà possibile eseguire il ricollegamento automatico. La necessità di eseguire la ricompilazione manualmente viene segnalata con un apposito messaggio.

 Le librerie statiche non vengono ricompilate in modalità Modifica e continuazione. Se si apportano modifiche a una libreria statica con Modifica e continuazione, è necessario ricompilare manualmente la libreria e ricollegare le app che la usano.

 Le istruzioni di compilazione personalizzate non vengono richiamate in modalità Modifica e continuazione. Se il programma usa istruzioni di compilazione personalizzate, sarà possibile effettuare manualmente la ricompilazione affinché tali istruzioni possano essere richiamate. In tal caso, è possibile disabilitare il ricollegamento dopo Modifica e continuazione per fare in modo che venga chiesto se si desidera procedere alla ricompilazione manuale.

 **Per disabilitare il ricollegamento dopo Modifica e continuazione**

1. Scegliere **Opzioni e impostazioni** dal menu **Debug**.

2. Nella finestra di dialogo **Opzioni** nel nodo **Debug** selezionare il nodo **Modifica e continuazione** .

3. Deselezionare la casella di controllo **Ricollega modifiche del codice dopo il debug** .

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> Limitazioni dell'intestazione precompilata
 Per impostazione predefinita, in Modifica e continuazione le intestazioni precompilate vengono caricate ed elaborate in background per velocizzare l'elaborazione delle modifiche al codice. Il caricamento delle intestazioni precompilate richiede l'allocazione di memoria fisica, il che può rappresentare un problema se si effettua la compilazione usando un computer che dispone di una quantità limitata di RAM. È possibile determinare se ciò può costituire un problema usando Gestione attività di Windows per verificare la quantità di memoria fisica disponibile durante il debug. Se la quantità di memoria supera le dimensioni delle intestazioni precompilate, Modifica e continuazione non dovrebbe presentare alcun problema. Se tale quantità è inferiore alle dimensioni delle intestazioni precompilate, è possibile configurare Modifica e continuazione in modo da evitare che le intestazioni precompilate vengano caricate in background.

 **Per disabilitare il caricamento in background delle intestazioni precompilate da parte di Modifica e continuazione**

1. Scegliere **Opzioni e impostazioni** dal menu **Debug**.

2. Nella finestra di dialogo **Opzioni** nel nodo **Debug** selezionare il nodo **Modifica e continuazione** .

3. Deselezionare la casella di controllo **Consenti precompilazione** .

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> Limitazioni degli attributi IDL
 Modifica e Continua non consentono di rigenerare file di definizione di interfaccia (IDL). Le modifiche agli attributi IDL non verranno pertanto riflesse mentre si esegue il debug. Per visualizzare il risultato delle modifiche agli attributi IDL è necessario interrompere il debug e ricompilare l'app. Se gli attributi IDL sono stati modificati, non verrà generato alcun errore o avviso. Per altre informazioni, vedere [Attributi IDL](/cpp/windows/idl-attributes).

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> Diagnosi dei problemi
 Se lo scenario non rientra nelle condizioni indicate in precedenza, è possibile raccogliere altri dettagli impostando il valore del Registro di sistema DWORD seguente:
 1. Aprire un Prompt dei comandi per gli sviluppatori.
 2. Eseguire il comando seguente: 
    ::: moniker range=">=vs-2022" 
     `VsRegEdit.exe set “C:\Program Files\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`
    ::: moniker-end
    ::: moniker range="vs-2019"
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`
    ::: moniker-end

 L'impostazione di questo valore all'inizio di una sessione di debug fa sì che i vari componenti di Modifica e continuazione spew registrazione dettagliata nel Finestra di output  >  **Debug.**

## <a name="see-also"></a>Vedi anche
- [Modifica e continuazione (C++)](../debugger/edit-and-continue-visual-cpp.md)
