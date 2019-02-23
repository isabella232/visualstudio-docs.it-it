---
title: Strumento Windows nel Registro di sistema | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adb79fec233171a0d20e817f9675aaab8e7228f8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693165"
---
# <a name="tool-windows-in-the-registry"></a>Strumento Windows nel Registro di sistema
Pacchetti VSPackage che forniscono finestre degli strumenti è necessario registrare con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] come strumento di provider di finestra. Finestre degli strumenti create utilizzando il modello di pacchetto di Visual Studio per eseguire questa operazione per impostazione predefinita. I provider di finestra degli strumenti hanno chiavi del Registro di sistema che specificano gli attributi di visibilità, ad esempio dimensioni della finestra degli strumenti predefinita e la posizione, il GUID della finestra che viene utilizzato come il riquadro della finestra degli strumenti e lo stile di ancoraggio.

 Durante lo sviluppo, i provider di finestra degli strumenti gestita registrare finestre degli strumenti aggiungendo attributi al codice sorgente e quindi eseguendo l'utilità RegPkg.exe sull'assembly risultante. Per altre informazioni, vedere [la registrazione di una finestra degli strumenti](../extensibility/registering-a-tool-window.md).

## <a name="registering-unmanaged-tool-window-providers"></a>Registrazione dei provider di finestra degli strumenti non gestito
 Provider di finestra degli strumenti non gestito è necessario registrare con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nella sezione ToolWindows del Registro di sistema. Il frammento di file con estensione reg seguente mostra come potrebbe essere registrata una finestra degli strumenti dinamica:

```
- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"
"Float"="250, 250, 410, 430"
"DontForceCreate"=dword:00000001

- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000
```

 La prima chiave nell'esempio precedente, numero di versione è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ad esempio 7.1 o 8.0, la sottochiave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} è il GUID del riquadro della finestra degli strumenti (DynamicWindowPane) e {il valore predefinito 01069cdd-95ce-4620-ac21-ddff6c57f012} è il GUID del pacchetto VSPackage per consentire la finestra degli strumenti. Per una spiegazione delle sottochiavi di tipo Float e DontForceCreate, vedere [configurazione visualizzazione della finestra degli strumenti](../extensibility/tool-window-display-configuration.md).

 La seconda chiave facoltativa, ToolWindows\Visibility, specifica il GUID dei comandi che richiedono la finestra degli strumenti deve essere reso visibile. In questo caso, non esistono Nessun comando specificato. Per altre informazioni, vedere [configurazione visualizzazione della finestra degli strumenti](../extensibility/tool-window-display-configuration.md).

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)