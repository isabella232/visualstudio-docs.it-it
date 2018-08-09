---
title: Eseguire la migrazione di registrazione della classe COM del debugger a 64 bit | Microsoft Docs
ms.custom: ''
ms.date: 11/10/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: douge
ms.workload:
- greggm
ms.openlocfilehash: 6c7578ddbdf84a1520a732fb64380bb53e5359f9
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637851"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Eseguire la migrazione a 64 bit del debugger registrazione della classe COM

Le classi tramite regasm, regsvr32, o scrivendo direttamente nel Registro di sistema e caricati in per le estensioni del debugger che registrano COM HKEY_CLASSES_ROOT *msvsmon.exe* (il debugger remoto), è ora possibile fornirlo registrazione a msvsmon senza la necessità di scrivere in HKEY_CLASSES_ROOT. Questo influisce sulle analizzatori di espressioni del debugger .NET legacy oppure motori di debug che sono configurati per il caricamento nel *msvsmon.exe* processo.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Per usare questa tecnica, aggiungere un  **.msvsmon-comclass-def.json* file accanto a msvsmon (InstallDir:* \Common7\IDE\Remote Debugger\x64*).

Ecco un file di msvsmon-comclass-def di esempio che registra uno gestito e una classe nativa:

Nome file: *MyCompany.MyExample.msvsmon-comclass-def.json*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
