---
description: Di seguito sono riportate le enumerazioni per Visual Studio Debugging SDK.
title: Enumerazioni (Visual Studio debug) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerations [Visual Studio SDK]
- debugging [Debugging SDK], enumerations
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ee22e24dc2bb8047cec6e9fd96c4b978ed5eb3c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145575"
---
# <a name="enumerations-visual-studio-debugging"></a>Enumerazioni (debug di Visual Studio)
Di seguito sono riportate le enumerazioni per [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l'SDK di debug.

- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md) Specifica come interpretare un ID processo nella [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura .

- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Specifica i tipi di un indirizzo.

- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) Specifica la posizione di un assembly.

- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) Specifica il motivo per cui il motore di debug (DE) si connette a un nodo di programma.

- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) Specifica lo stile della condizione del punto di interruzione per i punti di interruzione in sospeso e associati.

- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) Specifica il tipo di errore di un punto di interruzione.

- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Fornisce flag facoltativi che possono essere utilizzati per specificare informazioni aggiuntive durante l'impostazione di un punto di interruzione.

- [BP_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md) Enumera i valori validi per i flag facoltativi che possono essere utilizzati per specificare informazioni aggiuntive durante l'impostazione di un punto di interruzione. Questa enumerazione estende [](../../../extensibility/debugger/reference/bp-flags.md) l BP_FLAGS enumere.

- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) Specifica il tipo di posizione del punto di interruzione per una richiesta di punto di interruzione.

- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) Specifica la condizione associata al numero di passaggi del punto di interruzione che causerà l'avvio del punto di interruzione.

- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) Specifica se il punto di interruzione dei dati viene emulato o implementato nell'hardware.

- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Specifica l'esistenza di un punto di interruzione associato e se è abilitato.

- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) Specifica se il punto di interruzione si trova in una posizione del codice, è un percorso dati o è un altro tipo di punto di interruzione.

- [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) Indica il motivo per cui un punto di interruzione è stato scollegato.

- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) Specifica le informazioni da recuperare su una risoluzione non riuscita di un punto di interruzione.

- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Specifica le informazioni da recuperare su una richiesta di punto di interruzione.

- [BPREQI_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md) Enumera i valori validi che specificano le informazioni da recuperare su una richiesta di punto di interruzione. Questa enumerazione estende [l'BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumerazione .

- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) Specifica quali informazioni devono essere recuperate sulla risoluzione corretta di un punto di interruzione.

- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) Utilizzato per determinare se un programma può arrestare l'esecuzione dopo aver raggiunto un punto specifico dell'esecuzione.

- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) Valore che indica il protocollo utilizzato per comunicare tra un server di debug e il pacchetto di debug.

- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) Seleziona tipi diversi di costruttori.

- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) Specifica i criteri per confrontare due contesti di memoria.

- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) Specifica le informazioni da recuperare su un contesto di memoria.

- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Descrive vari attributi per [un'interfaccia IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) o [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) Specifica il motivo per cui il processo è stato avviato per il debug.

- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Specifica le informazioni da recuperare su un oggetto proprietà di debug.

- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Specifica le informazioni da recuperare su un oggetto di riferimento di debug.

- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) Specifica i flag per disassembly.

- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Specifica le informazioni da recuperare su un campo disassembly.

- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) Specifica l'ambito del flusso disassembly.

- [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) Enumera i valori validi che rappresentano i tipi di informazioni da ottenere da un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e visualizzarli all'utente.

- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) Specifica i criteri per confrontare due contesti di documento.

- [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) Specifica la quantità di stato di un programma di cui eseguire il dump.

- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Specifica come interpretare il tipo di un [oggetto IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) Rappresenta i motivi per cui Modifica e continuazione non è disponibile.

- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) Specifica i flag che controllano la valutazione delle espressioni.

- [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md) Enumera i valori validi per i flag che controllano la valutazione dell'espressione. Questa enumerazione estende [l'enumerazione EVALFLAGS.](../../../extensibility/debugger/reference/evalflags.md)

- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) Specifica gli attributi dell'evento.

- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Specifica lo stato dell'eccezione.

- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Specifica le informazioni da recuperare su un [oggetto IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Specifica il tipo di campo contenuto in un [oggetto IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

- [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) Enumera tipi aggiuntivi di campi che un [oggetto IDebugField](../../../extensibility/debugger/reference/idebugfield.md) può contenere. Questa enumerazione estende [](../../../extensibility/debugger/reference/field-kind.md) l FIELD_KIND enumere.

- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Specifica i modificatori per un tipo di campo.

- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Specifica le informazioni da recuperare su un oggetto stack frame specificato.

- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) Specifica il tipo di nome host.

- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) Specifica il tipo di nome dei file da recuperare.

- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) Specifica le azioni da intraprendere durante l'intercettazione delle eccezioni.

- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) Specifica la modalità di avvio di un programma.

- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) Specifica il tipo di informazioni da recuperare per un computer specifico.

- [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) Usato per descrivere un computer.

- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) Specifica il tipo di messaggio e il motivo.

- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) Usato per descrivere un modulo.

- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Specifica i flag per le informazioni sul modulo di debug.

- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Specifica lo stato dei simboli per un modulo.

- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) Seleziona l'opzione di distinzione tra maiuscole e minuscole per i nomi corrispondenti.

- [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Specifica il tipo di un oggetto dall'analizzatore di espressioni.

- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) Specifica come analizzare un'espressione.

- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) Specifica lo stato di un punto di interruzione in sospeso (un punto di interruzione che non è ancora stato associato).

- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) Specifica i flag di stato del punto di interruzione in sospeso.

- [PORT_SUPPLIER_DESCRIPTION_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md) Definisce i metadati che possono essere recuperati su un fornitore di porte.

- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) È stato specificato il tipo di informazioni da recuperare per un processo.

- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) Descrive o specifica le proprietà di un processo.

- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md) Enumera i valori validi dei flag di eliminazione programma.

- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) Specifica le proprietà associate a un provider di programmi.

- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) Specifica le proprietà desiderate da ottenere da un provider di programmi.

- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) Specifica il tipo di confronto per i riferimenti.

- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) Specifica il tipo di riferimento.

- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) Specifica la posizione da cui iniziare la ricerca in un disassembly.

- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) Specifica il tipo di passaggio per l'esecuzione di istruzioni.

- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) Specifica l'unità di passaggio per l'esecuzione di istruzioni.

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) Specifica il tipo di informazioni sui simboli da recuperare.

- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) Descrive gli attributi di un documento.

- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Specifica le informazioni su un thread da recuperare.

- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) Specifica lo stato del thread.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h, sh.h o ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
