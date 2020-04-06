---
title: Proprietà IDebugSymbolProvider . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719176"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Questa interfaccia rappresenta un provider di simboli che fornisce simboli e tipi, restituendoli come campi.

## <a name="syntax"></a>Sintassi

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Un provider di simboli deve implementare questa interfaccia per fornire informazioni sui simboli e sul tipo a un analizzatore di espressioni.

## <a name="notes-for-callers"></a>Note per i chiamanti
Questa interfaccia viene ottenuta `CoCreateInstance` utilizzando la funzione com(per i provider di simboli non gestiti) o caricando l'assembly di codice gestito appropriato e la creazione di un'istanza del provider di simboli in base alle informazioni presenti in tale assembly. Il motore di debug crea un'istanza del provider di simboli per lavorare in coordinamento con l'analizzatore di espressioni. Vedere l'esempio per un approccio alla creazione di istanze di questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono `IDebugSymbolProvider`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|`Initialize`|Operazione deprecata. Non usare.|
|`Uninitialize`|Operazione deprecata. Non usare.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ottiene il campo che contiene l'indirizzo di debug.|
|`GetField`|Operazione deprecata. Non usare.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Esegue il mapping di una posizione di documento in una matrice di indirizzi di debug.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Esegue il mapping di un contesto di documento in una matrice di indirizzi di debug.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Esegue il mapping di un indirizzo di debug in un contesto di documento.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ottiene il linguaggio utilizzato per compilare il codice in corrispondenza dell'indirizzo di debug.|
|`GetGlobalContainer`|Operazione deprecata. Non usare.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Ottiene il campo che rappresenta un nome di metodo completo.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Ottiene il tipo di campo di classe che rappresenta un nome di classe completo.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crea un enumeratore per gli spazi dei nomi associati all'indirizzo di debug.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Esegue il mapping di un nome di simbolo a un tipo di simbolo.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Ottiene l'indirizzo di debug che segue un determinato indirizzo di debug in un metodo.|

## <a name="remarks"></a>Osservazioni
Questa interfaccia esegue il mapping delle posizioni dei documenti negli indirizzi di debug e viceversa.

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
In questo esempio viene illustrato come creare un'istanza del provider di simboli, dato il relativo GUID (un motore di debug deve conoscere questo valore).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
