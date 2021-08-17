---
title: Strutture e unioni | Microsoft Docs
description: Questo articolo contiene collegamenti a descrizioni di riferimento di strutture e unioni nell'SDK di Visual Studio Debugging SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a5ac418731fc3676c4813ff3e346f452342f7df9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057395"
---
# <a name="structures-and-unions"></a>Strutture e unioni
Di seguito sono riportate le strutture e le unioni nell'SDK Visual Studio debug.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Specifica l'ID processo, che può essere un ID di sistema o un GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Descrive le condizioni in cui verrà generato un punto di interruzione.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Descrive la risoluzione di un punto di interruzione degli errori, tra cui posizione, programma e thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Specifica il tipo di struttura utilizzato per descrivere la posizione del punto di interruzione.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Definisce i componenti che descrivono la posizione di un punto di interruzione in corrispondenza di un indirizzo nel codice.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Descrive la posizione di un punto di interruzione associato direttamente a un indirizzo nel programma in fase di debug.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Descrive il percorso di un punto di interruzione in corrispondenza della riga in un file di origine del codice.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Descrive la posizione di offset di un punto di interruzione in corrispondenza di una funzione nel codice.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Usato per impostare punti di interruzione del codice in base a una stringa che l'utente può immettere dall'IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Usato per impostare punti di interruzione dei dati basati su una stringa che l'utente può immettere dall'IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Descrive la risoluzione di un punto di interruzione in una posizione specifica.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Descrive il conteggio e le condizioni su cui verrà attivato un punto di interruzione dopo essere stato passato in precedenza.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Contiene le informazioni necessarie per implementare un punto di interruzione.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Contiene le informazioni necessarie per implementare un punto di interruzione ,come la [struttura](../../../extensibility/debugger/reference/bp-request-info.md) BP_REQUEST_INFO, ma include informazioni sul GUID del fornitore, sul vincolo e sul punto di traccia.

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Descrive la posizione di un punto di interruzione del codice.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Descrive il risultato dell'associazione di un punto di interruzione dati.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Descrive le informazioni sui punti di interruzione associati per un punto di interruzione del codice o un punto di interruzione dati.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Specifica la struttura della posizione di risoluzione del punto di interruzione.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Descrive una matrice di stringhe.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Specifica informazioni su un tipo di campo tratto dai metadati.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Descrive una chiamata a una funzione o a un metodo.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Descrive il computer in cui è in esecuzione il debugger.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Descrive un elenco di GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Descrive un contesto di memoria o di codice.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Descrive un indirizzo in un programma in fase di debug.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Rappresenta uno dei diversi tipi di indirizzi.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identifica un visualizzatore personalizzato o un visualizzatore di tipi.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Descrive una proprietà di debug che a sua volta descrive un oggetto di natura gerarchica con nome, tipo e valore.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Descrive un riferimento.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Descrive il disassembly nell'IDE per la visualizzazione.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Descrive un'eccezione o un errore di run-time generato dal programma in fase di debug.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Descrive una variabile locale, un parametro o un altro campo.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Descrive un stack frame.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Descrive una matrice di identificatori univoci per i motori di debug disponibili.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Usato per impostare le informazioni di JustMyCode per un modulo.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Descrive un computer specifico.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Descrive un elemento di matrice all'interno di una matrice.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Descrive l'indirizzo di un campo di una classe o di una struttura.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Descrive l'indirizzo di una variabile locale all'interno di un ambito (in genere una funzione o un metodo).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Descrive l'indirizzo di un metodo di una classe.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Descrive un parametro di un metodo o di una funzione.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Descrive un valore restituito da un metodo o una funzione.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Descrive un tipo di campo tratto dai metadati.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Descrive un modulo specifico (DLL, EXE o assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Descrive le informazioni sullo stato dei percorsi di ricerca dei simboli in cui è stata ricercata.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Descrive un indirizzo nativo.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Descrive un tipo di campo tratto da un simbolo PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Descrive lo stato di un punto di interruzione pronto per l'associazione a una posizione del codice.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Descrive un processo.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Descrive un elenco di oggetti [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che rappresentano i nodi del programma.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Descrive i processi in esecuzione in un computer.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Descrive la posizione della riga e della colonna nel testo specificato.

- [PROPRIETÀ THREAD](../../../extensibility/debugger/reference/threadproperties.md) Descrive le proprietà di un thread.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Descrive il tipo di un campo.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Descrive un indirizzo fisico.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Descrive un indirizzo relativo a un puntatore `this` ( `Me` in Visual Basic).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h, sh.h o ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
