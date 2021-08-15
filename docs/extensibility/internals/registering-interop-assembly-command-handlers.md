---
title: Registrazione dei gestori dei comandi degli assembly di interoperabilità | Microsoft Docs
description: Informazioni sul contratto di comando di base usato da tutti i pacchetti VSPackage che implementano i comandi usando assembly di interoperabilità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 65456c5d351bda47663b93e450c938b030a68bf9086e137540c632c67599ffab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275281"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrazione dei gestori dei comandi negli assembly di interoperabilità
Un VSPackage deve registrarsi con in modo che l'ambiente di sviluppo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrato (IDE) instrada correttamente i comandi.

 Il Registro di sistema può essere aggiornato tramite modifica manuale o tramite un file di registrazione (con estensione rgs). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Managed Package Framework (MPF) fornisce questa funzionalità tramite la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe .

- [Le risorse di riferimento per il formato della](/previous-versions/bb164647(v=vs.100)) tabella dei comandi si trovano nelle DLL dell'interfaccia utente satellite non gestite.

## <a name="command-handler-registration-of-a-vspackage"></a>Registrazione del gestore comandi di un pacchetto VSPackage
 Un VSPackage che funge da gestore per i comandi basati sull'interfaccia utente richiede una voce del Registro di sistema denominata in base a VSPackage `GUID` . Questa voce del Registro di sistema specifica il percorso del file di risorse dell'interfaccia utente del pacchetto VSPackage e la risorsa di menu all'interno di tale file. La voce del Registro di sistema si trova in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\Menus, dove è la versione di \\ *\<Version>* , ad esempio *\<Version>* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 9.0.

> [!NOTE]
> Il percorso radice del HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudiopuò essere sostituito con una radice alternativa \\ *\<Version>* quando la shell viene [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inizializzata. Per altre informazioni sul percorso radice, vedere [Installing VSPackages With Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Voce del Registro di sistema delle risorse CTMENU
 La struttura della voce del Registro di sistema è:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> è `GUID` l'oggetto del pacchetto VSPackage nel formato {XXXXXX-XXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *\<Resource Information>* è costituito da tre elementi separati da virgole. Questi elementi sono, nell'ordine seguente:

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 Nella tabella seguente vengono descritti i campi di \<*Resource Information*> .

| Elemento | Descrizione |
|---------------------------| - |
| \<*Path to Resource DLL*> | Si tratta del percorso completo della DLL di risorse che contiene la risorsa di menu o viene lasciato vuoto, a indicare che deve essere usata la DLL di risorse del VSPackage (come specificato nella sottochiave Packages in cui è registrato il pacchetto VSPackage stesso).<br /><br /> È insoddizionato lasciare vuoto questo campo. |
| \<*Menu Resource ID*> | Si tratta dell'ID risorsa della risorsa che contiene tutti gli elementi dell'interfaccia utente per il pacchetto VSPackage compilati `CTMENU` da un file con estensione [vsct.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Menu Version*> | Si tratta di un numero usato come versione per la `CTMENU` risorsa. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa questo valore per determinare se è necessario rimergerne il contenuto con `CTMENU` la cache di tutte le `CTMENU` risorse. Un rimerge viene attivato eseguendo il comando devenv setup.<br /><br /> Questo valore deve essere inizialmente impostato su 1 e incrementato dopo ogni modifica nella risorsa e prima che si verifichi `CTMENU` il rimerge. |

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