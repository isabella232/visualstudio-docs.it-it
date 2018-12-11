---
title: La registrazione dei gestori di comando di Assembly di interoperabilità | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a087b5952b930145cd9f620a0eebeeee5d947149
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778592"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrazione dei gestori dei comandi negli assembly di interoperabilità
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un pacchetto VSPackage è necessario registrare con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in modo che l'ambiente di sviluppo integrato (IDE) consente di indirizzare i comandi in modo corretto.  
  
 Il Registro di sistema può essere aggiornato mediante la modifica manuale o mediante un file di programma di registrazione (RGS). Per altre informazioni, vedere [Creating Registrar Scripts](http://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
 Il Framework di pacchetto gestito (MPF) fornisce questa funzionalità tramite i <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.  
  
 [Comando riferimento sul formato di tabella](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f) le risorse si trovano nelle DLL di interfaccia utente satellite non gestita.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Registrazione del gestore comando di un pacchetto VSPackage  
 Un pacchetto VSPackage che agisce come un gestore per l'interfaccia utente (UI)-comandi basati su richiede una voce del Registro di sistema denominata dopo che il pacchetto VSPackage `GUID`. Questa voce del Registro di sistema specifica il percorso del file di risorse del pacchetto VSPackage dell'interfaccia utente e la risorsa di menu all'interno del file. La voce del Registro di sistema stesso si trova sotto HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<versione >* \Menus, dove  *\<versione >* è la versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], ad esempio 9.0.  
  
> [!NOTE]
>  Il percorso radice di HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >* può essere sostituito con un'alternativa radice quando il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell viene inizializzata. Per altre informazioni sul percorso radice, vedere [installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
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
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|\<*Percorso DLL della risorsa*>|Questo è il percorso completo di DLL che contiene la risorsa di menu della risorsa o questo viene lasciato vuoto, che indica che la risorsa del VSPackage DLL deve essere utilizzato (come specificato nella sottochiave pacchetti in cui è registrato il pacchetto VSPackage stesso).<br /><br /> È facoltativa per lasciare vuoto questo campo.|  
|\<*ID risorsa di menu*>|Questo è l'ID della risorsa il `CTMENU` risorsa che contiene tutti gli elementi dell'interfaccia utente per il pacchetto VSPackage come compilato da un [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) file.|  
|\<*Versione di menu*>|Questo è un numero utilizzato come una versione per il `CTMENU` risorsa. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Usa questo valore per determinare se è necessario unire di nuovo le il contenuto del `CTMENU` con la cache di tutte le risorse `CTMENU` risorse. Un unire di nuovo le viene attivata eseguendo il comando setup devenv.<br /><br /> Questo valore deve essere inizialmente impostato su 1 e incrementato dopo ogni modifica apportata al `CTMENU` resource e prima di unire di nuovo le si verifica.|  
  
### <a name="example"></a>Esempio  
 Di seguito è riportato un esempio di un paio di voci di risorsa:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

