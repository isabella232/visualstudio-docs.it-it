---
title: Interfaccia IWefDebuggingSupport
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a4883d36c1833c66a2539380184521b070f5c2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544729"
---
# <a name="iwefdebuggingsupport-interface"></a>Interfaccia IWefDebuggingSupport
  Implementata da un ambiente di debug, ad esempio Visual Studio, per facilitare il debug delle app per Office. L'applicazione di Office, ad esempio Word o Excel, ottiene questa interfaccia da Visual Studio e quindi chiama i metodi sull'interfaccia in determinati punti durante la sessione di debug.

## <a name="syntax"></a>Sintassi

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Metodi
 Nella tabella seguente sono elencati i metodi definiti dall'Interfaccia IWefDebuggingSupport.

|Name|Descrizione|
|----------|-----------------|
|[Metodo GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Ottiene informazioni sulle app per Office che devono essere inserite automaticamente durante il debug.|
|[Metodo SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornisce l'identificatore del processo che eseguirà il contenuto del framework Web Extensions (WEF).|
