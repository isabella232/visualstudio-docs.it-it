---
title: Eseguire la migrazione della registrazione della classe COM del debugger a 64 bit| Microsoft Docs
description: Informazioni su come registrare classi COM in msvsmon per le estensioni del debugger senza scrivere in HKEY_CLASSES_ROOT.
ms.custom: SEO-VS-2020
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- greggm
ms.openlocfilehash: a9b569f78720d59bf6321ff972bd7f2668ca6729
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152120"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Eseguire la migrazione della registrazione della classe COM del debugger a 64 bit

Per le estensioni del debugger che registrano classi COM in HKEY_CLASSES_ROOT usando regasm, regsvr32 o scrivendo direttamente nel Registro di sistema e caricate *inmsvsmon.exe* (il debugger remoto), è ora possibile fornire questa registrazione a msvsmon senza dover scrivere in HKEY_CLASSES_ROOT. Ciò influisce sugli analizzatori di espressioni del debugger .NET legacy o sui motori di debug configurati per il caricamento *nelmsvsmon.exe* processo.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Per usare questa tecnica, aggiungere un.msvsmon-comclass-def.jssul file accanto a *msvsmon (InstallDir:* \Common7\IDE\Remote Debugger\x64*).

Di seguito è riportato un file msvsmon-comclass-def di esempio che registra una classe gestita e una classe nativa:

FileName: *MyCompany.MyExample.msvsmon-comclass-def.jssu*

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
