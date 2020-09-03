---
title: Modifiche al codice supportate (C++) | Microsoft Docs
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: af6c0d88dd230bee768641905e200f1f47749d77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77629586"
---
# <a name="supported-code-changes-c"></a>Modifiche al codice supportate (C++)
Modifica e continuazione per i progetti C++ gestisce la maggior parte dei tipi di modifiche al codice. Alcune modifiche non possono tuttavia essere applicate durante l'esecuzione del programma. Per applicare tali modifiche, è necessario arrestare l'esecuzione e compilare una versione aggiornata del codice.

 Per informazioni sull'uso di modifica e continuazione per C++ in Visual Studio, vedere [modifica e continuazione (c++)](../debugger/edit-and-continue-visual-cpp.md) .

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Requisiti
### <a name="build-settings-project--properties"></a>Impostazioni di compilazione (Proprietà progetto >):
  1. **C/C++ > generale > formato delle informazioni di debug**: database di programma per modifica e continuazione ( `/ZI` )
  2. **C/C++ > generazione di codice > Abilita ricompilazione minima**: Sì ( `/Gm` )
  3. **Linker > generale > Abilita collegamento incrementale**: Sì ( `/INCREMENTAL` )

     Eventuali impostazioni del linker non compatibili, ad esempio `/SAFESEH` o `/OPT:` ..., devono causare l'avviso _LNK4075_ durante la compilazione.  
     Esempio: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Impostazioni del debugger (opzioni di debug > > generale):
  - Abilita Modifica e continuazione nativo

     Eventuali impostazioni del compilatore o del linker non compatibili generano un errore durante la modifica e la continuazione.  
     Esempio: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Modifiche non supportate
 Non è possibile applicare le seguenti modifiche di C/C++ durante una sessione di debug. Se si apportano queste modifiche e si tenta di applicare le modifiche al codice, nella finestra di **output** verrà visualizzato un messaggio di errore o di avviso.

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
  - Hanno un membro statico o globale.
  - Vengono passati a una funzione std::. In questo modo viene generata una violazione ODR genuina e viene restituito C1092.

- Le librerie statiche non vengono aggiornate con la funzionalità Modifica e continuazione. Se si apporta una modifica in una libreria statica, l'esecuzione continua con la versione precedente e non viene visualizzato alcun avviso.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Scenari non supportati
 Modifica e continuazione per C/C++ non è disponibile nei seguenti scenari di debug:

- Debug di applicazioni native compilate con [/Zo (Ottimizzare il debug)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Nelle versioni di Visual Studio precedenti a Visual Studio 2015 Update 1, debug di app o componenti di UWP. A partire da Visual Studio 2015 Update 1, è possibile usare modifica e continuazione nelle app C++ UWP e nelle app DirectX, perché ora supporta l' `/ZI` opzione del compilatore con l'  `/bigobj` opzione. È anche possibile usare Modifica e continuazione con file binari compilati con l'opzione `/FASTLINK` .

- Debug di app dello Store 8/8.1. Questi progetti usano il set di strumenti VC 120 e l'opzione C/C++ `/bigobj` . La funzionalità modifica e continuazione con `/bigobj` è supportata solo nel set di strumenti VC 140.

- Debug in Windows 98.

- Debug in modalità mista (nativo/gestito).

- Debug JavaScript.

- Debug SQL.

- Debug di un file dump.

- Modifica di codice dopo un'eccezione non gestita, quando l'opzione **Rimuovi stack di chiamate su eccezioni non gestite** non è selezionata.

- Debug di un'app usando **Connetti a** invece di eseguire l'app da **Start** nel menu **Debug** .

- Debug di codice ottimizzato.

- Debug di una versione precedente del codice dopo l'esito negativo della compilazione di una nuova versione a causa di errori di compilazione.

- Utilizzando un percorso del compilatore (*cl.exe*) personalizzato. Per motivi di sicurezza, per la ricompilazione di un file durante la modifica e la continuazione, Visual Studio usa sempre il compilatore installato. Se si usa un percorso del compilatore personalizzato, ad esempio tramite una variabile personalizzata `$(ExecutablePath)` nel `*.props` file, viene visualizzato un avviso e Visual Studio esegue il fallback all'uso del compilatore installato della stessa versione/architettura.

- Sistema di compilazione FASTBuild. FASTBuild non è attualmente compatibile con l'opzione del compilatore "Abilita ricompilazione minima ( `/Gm` )" e quindi la funzionalità modifica e continuazione non è supportata.

- Architetture legacy/set di strumenti VC. Con il set di strumenti VC 140, il debugger predefinito supporta modifica e continuazione con le applicazioni x86 e x64. I set di strumenti legacy supportano solo applicazioni x86. I set di strumenti più vecchi di VC 120 devono usare il debugger legacy selezionando "_Opzioni di Debug > > generale >_ usare la modalità di compatibilità nativa" per usare modifica e continuazione.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Limitazioni di collegamento

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opzioni dei linker che disabilitano Modifica e continuazione
 La funzionalità Modifica e continuazione viene disabilitata dalle seguenti opzioni dei linker:

- L'impostazione di **/OPT:REF**, **/OPT:ICF**o **/INCREMENTAL:NO** provoca la disattivazione di Modifica e continuazione con la visualizzazione del seguente messaggio di avviso:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- L'impostazione di **/Order**, **/Release**o **/Force** Disabilita la modifica e continua con l'avviso seguente:  
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
 Se lo scenario non rientra nelle condizioni indicate in precedenza, è possibile raccogliere ulteriori dettagli impostando il valore DWORD del registro di sistema seguente:
 1. Aprire un Prompt dei comandi per gli sviluppatori.
 2. Eseguire il comando seguente:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Se si imposta questo valore all'inizio di una sessione di debug, i vari componenti di modifica e continuazione generano una registrazione **Output Window**dettagliata nel riquadro di  >  **debug** finestra di output.

## <a name="see-also"></a>Vedere anche
- [Modifica e continuazione (C++)](../debugger/edit-and-continue-visual-cpp.md)
