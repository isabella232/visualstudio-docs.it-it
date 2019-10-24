---
title: Registrazione di gestori di comandi di assembly di interoperabilità | Microsoft Docs
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
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724694"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrazione dei gestori dei comandi negli assembly di interoperabilità
Un pacchetto VSPackage deve registrarsi con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modo che l'Integrated Development Environment (IDE) instrada i comandi correttamente.

 Il registro di sistema può essere aggiornato tramite la modifica manuale o tramite un file di registrazione (con estensione RGS). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Il Framework di pacchetto gestito (MPF) fornisce questa funzionalità tramite la classe <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>.

- Le risorse di riferimento per il [formato della tabella comandi](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) si trovano in DLL dell'interfaccia utente satellite non gestite.

## <a name="command-handler-registration-of-a-vspackage"></a>Registrazione del gestore comandi di un pacchetto VSPackage
 Un pacchetto VSPackage che funge da gestore per i comandi basati su interfaccia utente richiede una voce del registro di sistema denominata dopo il VSPackage `GUID`. Questa voce del registro di sistema specifica il percorso del file di risorse dell'interfaccia utente del pacchetto VSPackage e della risorsa di menu all'interno del file. La voce del registro di sistema si trova in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ *\<Version >* \Menus, dove *\<Version >* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ad esempio 9,0.

> [!NOTE]
> Il percorso radice di HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<Version >* può essere sottoposto a override con una radice alternativa quando viene inizializzata la shell [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni sul percorso radice, vedere [installazione di VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Voce del registro di sistema della risorsa CTMENU
 La struttura della voce del registro di sistema è:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> è il `GUID` di VSPackage nel formato {xxxxxx-XXXX-XXXX-XXXX-xxxxxxxxx}.

 *\<Resource informazioni >* è costituito da tre elementi separati da virgole. Questi elementi sono, nell'ordine:

 \<*percorso della dll della risorsa*>,*ID risorsa menu*\< >, \<*versione menu* >

 Nella tabella seguente vengono descritti i campi di \<*informazioni sulle risorse*>.

| Elemento | Descrizione |
|---------------------------| - |
| \<*percorso della dll della risorsa* > | Si tratta del percorso completo della DLL di risorse che contiene la risorsa di menu o viene lasciato vuoto, a indicare che è necessario usare la DLL di risorse del pacchetto VSPackage (come specificato nella sottochiave pacchetti in cui è registrato il pacchetto VSPackage).<br /><br /> È personalizzato per lasciare vuoto questo campo. |
| *ID risorsa Menu* \< > | Si tratta dell'ID risorsa della risorsa `CTMENU` che contiene tutti gli elementi dell'interfaccia utente per il pacchetto VSPackage compilato da un file con [estensione vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) . |
| \<*versione Menu* > | Si tratta di un numero usato come versione per la risorsa `CTMENU`. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizza questo valore per determinare se è necessario riunire il contenuto della risorsa `CTMENU` con la relativa cache di tutte le risorse di `CTMENU`. Viene attivata una riunione eseguendo il comando di configurazione devenv.<br /><br /> Questo valore deve essere inizialmente impostato su 1 e incrementato dopo ogni modifica nella risorsa `CTMENU` e prima che venga eseguita la riunione. |

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio di un paio di voci di risorse:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Vedere anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)