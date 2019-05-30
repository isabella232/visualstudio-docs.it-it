---
title: Enumerazioni (debug di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerations [Visual Studio SDK]
- debugging [Debugging SDK], enumerations
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cc4f811c1b1651d6ac5807f754a2d9c97eda2ad
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337891"
---
# <a name="enumerations-visual-studio-debugging"></a>Enumerazioni (debug di Visual Studio)
Di seguito sono le enumerazioni per il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging SDK.

- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md) specifica come interpretare un ID di processo nel [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura.

- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) specifica i tipi di un indirizzo.

- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) specifica in cui si trova un assembly.

- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) specifica il motivo per il motore di debug (DE) da associare a un nodo di programma.

- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) specifica la condizione di punto di interruzione in sospeso di stile per e associati i punti di interruzione.

- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) specifica il tipo di errore di un punto di interruzione.

- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) fornisce flag facoltativo che può essere usato per specificare informazioni aggiuntive durante l'impostazione di un punto di interruzione.

- [BP_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md) enumera i valori validi per i flag facoltativi che possono essere usati per specificare informazioni aggiuntive durante l'impostazione di un punto di interruzione. Questa enumerazione estende la [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumerazione.

- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) specifica il tipo di posizione del punto di interruzione per una richiesta di punto di interruzione.

- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) specifica la condizione associata con il punto di interruzione pass che determinerà il punto di interruzione da attivare.

- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) specifica se il punto di interruzione dei dati viene emulato o implementata nell'hardware.

- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) specifica l'esistenza di un punto di interruzione associato e se è abilitato.

- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) specifica se il punto di interruzione si trova in una posizione di codice, è un percorso dati o un altro tipo di punto di interruzione.

- [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) indica il motivo è stato dissociato un punto di interruzione.

- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) specifica le informazioni da recuperare su una risoluzione non riuscita di un punto di interruzione.

- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) specifica le informazioni da recuperare su una richiesta di punto di interruzione.

- [BPREQI_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md) enumera i valori validi che specificano le informazioni da recuperare su una richiesta di punto di interruzione. Questa enumerazione estende la [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumerazione.

- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) specifica quali informazioni sono necessario recuperare sulla corretta risoluzione di un punto di interruzione.

- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) utilizzato per determinare se un programma può arrestare l'esecuzione dopo aver raggiunto un punto particolare nell'esecuzione.

- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) un valore che indica il protocollo usato per la comunicazione tra un server di debug e il pacchetto di debug.

- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) consente di selezionare diversi tipi di costruttori.

- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) specifica i criteri per il confronto di due contesti di memoria.

- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) specifica le informazioni da recuperare su un contesto di memoria.

- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) descrive i vari attributi per un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) o un' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfaccia.

- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) specifica il motivo per cui è stato avviato il processo per eseguire il debug.

- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) specifica le informazioni da recuperare un oggetto di proprietà di debug.

- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) specifica le informazioni da recuperare un oggetto di riferimento di debug.

- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) specifica i flag per il disassembly.

- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) specifica le informazioni da recuperare relative a un campo disassembly.

- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) specifica l'ambito del flusso di disassemblaggio.

- [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) enumera i valori validi che rappresentano i tipi di informazioni da eseguire da un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) dell'oggetto e visualizzare all'utente.

- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) specifica i criteri per il confronto di due contesti di documento.

- [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) specifica la quantità di stato di un programma per eseguire il dump.

- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) specifica come interpretare il tipo di un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.

- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) rappresenta motivi per cui modifica e continuano non è disponibile.

- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) specifica i flag che controllano la valutazione dell'espressione.

- [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md) enumera i valori validi per i flag che controllano la valutazione dell'espressione. Questa enumerazione estende la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumerazione.

- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) specifica gli attributi dell'evento.

- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) specifica lo stato di eccezione.

- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) specifica le informazioni da recuperare su un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.

- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) specifica il tipo di campo contenuto un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.

- [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) enumera i tipi di campi aggiuntivi un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto può contenere. Questa enumerazione estende la [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) enumerazione.

- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) specifica modificatori per un tipo di campo.

- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) specifica le informazioni per recuperare un oggetto frame dello stack.

- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) specifica il tipo del nome host.

- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) specifica il tipo di nome di file da recuperare.

- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) specifica le azioni da intraprendere quando si intercetta le eccezioni.

- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) specifica come deve essere avviato un programma.

- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) specifica quale tipo di informazioni da recuperare per un computer specifico.

- [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) utilizzato per descrivere un computer.

- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) specifica il tipo di messaggio e il motivo.

- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) utilizzato per descrivere un modulo.

- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) specifica i flag per le informazioni del modulo di debug.

- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) specifica lo stato dei simboli per un modulo.

- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) seleziona l'opzione maiuscole per i nomi corrispondenti.

- [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) specifica il tipo di un oggetto dall'analizzatore di espressioni.

- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) specifica la modalità di analisi dell'espressione.

- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) specifica lo stato di un punto di interruzione in sospeso (un punto di interruzione che non è ancora stata associata).

- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) specifica i flag di stato punto di interruzione in sospeso.

- [PORT_SUPPLIER_DESCRIPTION_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md) definisce i metadati che possono essere recuperato su un fornitore di porte.

- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) specificato il tipo di informazioni da recuperare per un processo.

- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) descrizione o specifica le proprietà di un processo.

- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md) enumera validi i valori del programma di eliminare definitivamente i flag.

- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) specifica proprietà associate a un provider di programma.

- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) specifica le proprietà desiderate per essere ottenuto da un provider di programma.

- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) specifica il tipo di confronto per i riferimenti.

- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) specifica il tipo di riferimento.

- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) specifica la posizione da cui iniziare la ricerca nel disassembly.

- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) specifica il tipo di passaggio per l'esecuzione di istruzioni.

- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) specifica l'unità di incremento per l'esecuzione di istruzioni.

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) specifica il tipo di informazioni sui simboli da recuperare.

- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) vengono descritti gli attributi di un documento.

- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) specifica le informazioni relative a un thread che deve essere recuperato.

- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) specifica lo stato del thread.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h sh.h o ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)