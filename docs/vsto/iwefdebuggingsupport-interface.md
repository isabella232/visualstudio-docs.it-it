---
title: Interfaccia IWefDebuggingSupport
description: Informazioni su come usare un ambiente di debug come Visual Studio per facilitare il debug Microsoft Office applicazioni.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f6c6e039a04f8e30cec024370fed94c0f025f51f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147824"
---
# <a name="iwefdebuggingsupport-interface"></a>Interfaccia IWefDebuggingSupport
  Implementato da un ambiente di debug, ad esempio Visual Studio, per facilitare il debug delle app per Office. L Office appalto, ad esempio Word o Excel, ottiene questa interfaccia da Visual Studio e quindi chiama i metodi sull'interfaccia in determinati punti durante la sessione di debug.

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
 Nella tabella seguente sono elencati i metodi definiti dall'interfaccia IWefDebuggingSupport.

|Nome|Descrizione|
|----------|-----------------|
|[Metodo GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Ottiene informazioni sulle app per Office che devono essere inserite automaticamente durante il debug.|
|[Metodo SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornisce l'identificatore di processo che eseguirà il contenuto di Web Extensions Framework (WEF).|
