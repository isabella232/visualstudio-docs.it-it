---
title: La registrazione dei gestori di comando di Assembly di interoperabilità | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3e90ffc6b065b6d69bbe09bfe1887764ccc9955
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353328"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrazione dei gestori dei comandi negli assembly di interoperabilità
Un pacchetto VSPackage è necessario registrare con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modo che l'ambiente di sviluppo integrato (IDE) consente di indirizzare i comandi in modo corretto.

 Il Registro di sistema può essere aggiornato mediante la modifica manuale o mediante un file di programma di registrazione (RGS). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Il Framework di pacchetto gestito (MPF) fornisce questa funzionalità tramite i <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.

- [Comando riferimento sul formato di tabella](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) le risorse si trovano nelle DLL di interfaccia utente satellite non gestita.

## <a name="command-handler-registration-of-a-vspackage"></a>Registrazione del gestore comando di un pacchetto VSPackage
 Un pacchetto VSPackage che agisce come un gestore per l'interfaccia utente (UI)-comandi basati su richiede una voce del Registro di sistema denominata dopo che il pacchetto VSPackage `GUID`. Questa voce del Registro di sistema specifica il percorso del file di risorse del pacchetto VSPackage dell'interfaccia utente e la risorsa di menu all'interno del file. La voce del Registro di sistema stesso si trova sotto HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ *\<versione >* \Menus, dove  *\<versione >* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ad esempio 9.0.

> [!NOTE]
> Il percorso radice di HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<versione >* può essere sostituito con un'alternativa radice quando il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell viene inizializzata. Per altre informazioni sul percorso radice, vedere [installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>La voce del Registro di sistema di risorsa CTMENU
 La struttura della voce del Registro di sistema è:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> è il `GUID` del pacchetto VSPackage nel formato {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *\<Informazioni sulle risorse >* è costituito da tre elementi separati da virgole. Questi elementi sono, nell'ordine:

 \<*Percorso DLL della risorsa*>, \< *ID risorsa di Menu*>, \< *versione Menu*>

 Nella tabella seguente vengono descritti i campi di \< *informazioni sulle risorse*>.

| Elemento | Descrizione |
|---------------------------| - |
| \<*Percorso DLL della risorsa*> | Questo è il percorso completo di DLL che contiene la risorsa di menu della risorsa o questo viene lasciato vuoto, che indica che la risorsa del VSPackage DLL deve essere utilizzato (come specificato nella sottochiave pacchetti in cui è registrato il pacchetto VSPackage stesso).<br /><br /> È facoltativa per lasciare vuoto questo campo. |
| \<*ID risorsa di menu*> | Questo è l'ID della risorsa il `CTMENU` risorsa che contiene tutti gli elementi dell'interfaccia utente per il pacchetto VSPackage come compilato da un [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) file. |
| \<*Versione di menu*> | Questo è un numero utilizzato come una versione per il `CTMENU` risorsa. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Usa questo valore per determinare se è necessario unire di nuovo le il contenuto del `CTMENU` con la cache di tutte le risorse `CTMENU` risorse. Un unire di nuovo le viene attivata eseguendo il comando setup devenv.<br /><br /> Questo valore deve essere inizialmente impostato su 1 e incrementato dopo ogni modifica apportata al `CTMENU` resource e prima di unire di nuovo le si verifica. |

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio di un paio di voci di risorsa:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Vedere anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)