---
title: Strutture e Unioni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19d8f547d98488edffc6049be7619e5b5e921d93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713486"
---
# <a name="structures-and-unions"></a>Strutture e unioni
Di seguito sono riportate strutture e unioni in Visual Studio Debugging SDK.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Specifica l'ID processo, che può essere un ID di sistema o un GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Descrive le condizioni in cui verrà generato un punto di interruzione.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Viene descritta la risoluzione di un punto di interruzione di errore, inclusi percorso, programma e thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Specifica il tipo di struttura utilizzata per descrivere la posizione del punto di interruzione.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Definisce i componenti che descrivono la posizione di un punto di interruzione in corrispondenza di un indirizzo nel codice.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Descrive la posizione di un punto di interruzione associato direttamente a un indirizzo nel programma sottoposto a debug.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Descrive la posizione di un punto di interruzione in corrispondenza di un file di origine del codice.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Descrive la posizione di offset di un punto di interruzione in corrispondenza di una funzione nel codice.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Utilizzato per l'impostazione di punti di interruzione del codice in base a una stringa che l'utente può immettere dall'IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Utilizzato per l'impostazione di punti di interruzione di dati basati su una stringa che l'utente può immettere dall'IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Viene descritta la risoluzione di un punto di interruzione in una posizione specifica.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Descrive il conteggio e le condizioni su cui verrà generato un punto di interruzione dopo essere stato passato in precedenza.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Contiene le informazioni necessarie per implementare un punto di interruzione.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Contiene le informazioni necessarie per implementare un punto di interruzione (come la struttura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ma include il GUID del fornitore, il vincolo e le informazioni sul punto di traccia).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Descrive la posizione di un punto di interruzione del codice.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Viene descritto il risultato dell'associazione di un punto di interruzione dei dati.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Vengono descritte le informazioni sui punti di interruzione associati per un punto di interruzione del codice o un punto di interruzione di dati.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Specifica la struttura della posizione di risoluzione del punto di interruzione.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Descrive una matrice di stringhe.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Specifica le informazioni su un tipo di campo derivato dai metadati.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Descrive una chiamata a una funzione o a un metodo.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Descrive il computer in cui è in esecuzione il debugger.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Viene descritto un elenco di GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Descrive un contesto di memoria o di codice.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Descrive un indirizzo in un programma in fase di debug.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Rappresenta uno di diversi tipi di indirizzi.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identifica un visualizzatore o un visualizzatore di tipo personalizzato.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Descrive una proprietà di debug che a sua volta descrive un oggetto di natura gerarchica con nome, tipo e valore.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Descrive un riferimento.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Descrive il disassembly nell'IDE per la visualizzazione.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Viene descritta un'eccezione o un errore di run-time generato dal programma in fase di debug.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Descrive una variabile locale, un parametro o un altro campo.

- [INFO DI FRAME](../../../extensibility/debugger/reference/frameinfo.md) Descrive uno stack frame.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Descrive una matrice di identificatori univoci per i motori di debug disponibili.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Utilizzato per impostare le informazioni JustMyCode per un modulo.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Descrive un particolare computer.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Descrive un elemento della matrice all'interno di una matrice.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Descrive l'indirizzo di un campo di una classe o struttura.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Descrive l'indirizzo di una variabile locale all'interno di un ambito (in genere una funzione o un metodo).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Descrive l'indirizzo di un metodo di una classe.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Descrive un parametro di un metodo o di una funzione.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Descrive un valore restituito da un metodo o una funzione.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Descrive un tipo di campo derivato dai metadati.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Viene descritto un determinato modulo (DLL, EXE o assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Descrive le informazioni sullo stato dei percorsi di ricerca dei simboli in cui è stata eseguita la ricerca.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Descrive un indirizzo nativo.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Descrive un tipo di campo tratto da un simbolo PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Descrive lo stato di un punto di interruzione pronto per l'associazione a un percorso di codice.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Descrive un processo.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Viene descritto un elenco di [Oggetti IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che rappresentano i nodi del programma.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Descrive i processi in esecuzione su un computer.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Descrive la posizione della riga e della colonna nel testo specificato.

- [THREADPROPERTIES (PROPRIETÀ THREAD)](../../../extensibility/debugger/reference/threadproperties.md) Descrive le proprietà di un thread.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Descrive il tipo di un campo.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Descrive un indirizzo fisico.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Viene descritto un indirizzo relativo a un `this` puntatore (`Me` in Visual Basic).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h, sh.h o ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
