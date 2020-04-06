---
title: Registrazione dei gestori di comandi dell'assembly di interoperabilità Documenti Microsoft
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
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705866"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrazione dei gestori dei comandi negli assembly di interoperabilità
Un pacchetto VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve registrarsi con in modo che l'ambiente di sviluppo integrato (IDE) instrada correttamente i comandi.

 Il Registro di sistema può essere aggiornato mediante la modifica manuale o utilizzando un file di registrazione (RGs). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Il Framework di pacchetto gestito (MPF) fornisce questa funzionalità tramite la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.

- [Le](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) risorse di riferimento per il formato della tabella dei comandi si trovano nelle DLL dell'interfaccia utente satellite non gestite.

## <a name="command-handler-registration-of-a-vspackage"></a>Registrazione del gestore di comandi di un pacchetto VSPackageCommand Handler Registration of a VSPackage
 Un VSPackage che funge da gestore per i comandi basati sull'interfaccia utente richiede una voce del Registro di sistema denominata in base al pacchetto VSPackage `GUID`. Questa voce del Registro di sistema specifica il percorso del file di risorse dell'interfaccia utente del pacchetto VSPackage e la risorsa di menu all'interno di tale file. La voce del Registro di sistema stessa\\si trova nella cartella HKEY_LOCAL_MACHINE, Software, Microsoft VisualStudio*\<Version>* Menus, dove [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] * \<Versione>* è la versione di , ad esempio 9.0.

> [!NOTE]
> Quando>inizializzata la\\ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell, è possibile eseguire l'override del percorso di radice di HKEY_LOCAL_MACHINE , SOFTWARE , Microsoft VisualStudio*\<Version>.* Per ulteriori informazioni sul percorso radice, vedere [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Voce del Registro di sistema delle risorse CTMENUThe CTMENU Resource Registry Entry
 La struttura della voce del Registro di sistema è:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> `GUID` è il del pacchetto VSPackage nel formato XXXXXX-XXXX-XXXX-XXXX-XXXX-XXXXXXXXX.

 *Il>Informazioni sulle risorse è costituito da tre elementi separati da virgole. \<* Questi elementi sono, nell'ordine:

 \<*Percorso della DLL* \<di risorse>, *ID risorsa menu*>, \<Versione *menu*>

 Nella tabella seguente vengono \<descritti i campi della> *Informazioni sulle risorse.*

| Elemento | Descrizione |
|---------------------------| - |
| \<*Percorso della DLL delle risorse*> | Questo è il percorso completo della DLL di risorse che contiene la risorsa di menu o questo viene lasciato vuoto, che indica che la DLL di risorse del pacchetto VSPackage deve essere utilizzata (come specificato nella sottochiave Packages in cui è registrato il pacchetto VSPackage stesso).<br /><br /> È consuetudine lasciare vuoto questo campo. |
| \<*ID risorsa menu*> | Si tratta dell'ID `CTMENU` risorsa della risorsa che contiene tutti gli elementi dell'interfaccia utente per il pacchetto VSPackage come compilato da un file [con estensione vsct.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Versione menu*> | Si tratta di un numero `CTMENU` utilizzato come versione per la risorsa. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilizza questo valore per determinare se è necessario `CTMENU` riunire il `CTMENU` contenuto della risorsa con la cache di tutte le risorse. Una rimerge viene attivata eseguendo il comando devenv setup.<br /><br /> Questo valore deve inizialmente essere impostato su 1 `CTMENU` e incrementato dopo ogni modifica nella risorsa e prima che si verifichi nuovamente il merge. |

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio di un paio di voci di risorse:Here is an example of a couple of resource entries:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Vedere anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
