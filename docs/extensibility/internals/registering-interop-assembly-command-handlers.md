---
title: Registrazione di gestori di comandi di assembly di interoperabilità | Microsoft Docs
description: Informazioni sul contratto di comando di base usato da tutti i VSPackage che implementano i comandi usando assembly di interoperabilità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b45fe06722b190569e067dccd325ba4acac4fb0f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875154"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrazione dei gestori dei comandi negli assembly di interoperabilità
Un pacchetto VSPackage deve registrarsi in in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modo che il Integrated Development Environment (IDE) instrada correttamente i comandi.

 Il registro di sistema può essere aggiornato tramite la modifica manuale o tramite un file di registrazione (con estensione RGS). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Il Framework di pacchetto gestito (MPF) fornisce questa funzionalità tramite la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.

- Le risorse di riferimento per il [formato della tabella comandi](/previous-versions/bb164647(v=vs.100)) si trovano in DLL dell'interfaccia utente satellite non gestite.

## <a name="command-handler-registration-of-a-vspackage"></a>Registrazione del gestore comandi di un pacchetto VSPackage
 Un pacchetto VSPackage che funge da gestore per i comandi basati sull'interfaccia utente richiede una voce del registro di sistema denominata dopo il pacchetto VSPackage `GUID` . Questa voce del registro di sistema specifica il percorso del file di risorse dell'interfaccia utente del pacchetto VSPackage e della risorsa di menu all'interno del file. La voce del registro di sistema si trova in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ *\<Version>* \Menus, dove *\<Version>* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , ad esempio 9,0.

> [!NOTE]
> Il percorso radice di HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* può essere sottoposto a override con una radice alternativa quando la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell viene inizializzata. Per ulteriori informazioni sul percorso radice, vedere [installazione di VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Voce del registro di sistema della risorsa CTMENU
 La struttura della voce del registro di sistema è:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> è del `GUID` pacchetto VSPackage nel formato {xxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx}.

 *\<Resource Information>* è costituito da tre elementi separati da virgole. Questi elementi sono, nell'ordine:

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 Nella tabella seguente vengono descritti i campi di \<*Resource Information*> .

| Elemento | Descrizione |
|---------------------------| - |
| \<*Path to Resource DLL*> | Si tratta del percorso completo della DLL di risorse che contiene la risorsa di menu o viene lasciato vuoto, a indicare che è necessario usare la DLL di risorse del pacchetto VSPackage (come specificato nella sottochiave pacchetti in cui è registrato il pacchetto VSPackage).<br /><br /> È personalizzato per lasciare vuoto questo campo. |
| \<*Menu Resource ID*> | Si tratta dell'ID risorsa della `CTMENU` risorsa che contiene tutti gli elementi dell'interfaccia utente per il pacchetto VSPackage compilato da un file con [estensione vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) . |
| \<*Menu Version*> | Si tratta di un numero usato come versione per la `CTMENU` risorsa. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Usa questo valore per determinare se è necessario riunire il contenuto della `CTMENU` risorsa con la relativa cache di tutte le `CTMENU` risorse. Viene attivata una riunione eseguendo il comando di configurazione devenv.<br /><br /> Inizialmente, questo valore deve essere impostato su 1 e incrementato dopo ogni modifica nella `CTMENU` risorsa e prima che si verifichi il merge. |

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio di un paio di voci di risorse:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)