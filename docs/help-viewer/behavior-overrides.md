---
title: Override di Gestione contenuto della Guida
description: Informazioni sulle sostituzioni di Gestione contenuto della Guida, che modificano il comportamento predefinito di Help Viewer e delle funzionalità correlate alla Guida nell'IDE Visual Studio.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: 8d0838b648a08f430bbe917c9ec073b2760dfe0605f13a83a6ced5ef3e32040f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358662"
---
# <a name="help-content-manager-overrides"></a>Override di Gestione contenuto della Guida

È possibile modificare il comportamento predefinito di Help Viewer e le funzionalità correlate alla Guida nell'IDE di Visual Studio. Alcune opzioni vengono specificate mediante la creazione di un file con estensione [pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/) per impostare vari valori di chiavi del Registro di sistema. Altre vengono impostate direttamente nel Registro di sistema.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Come controllare il comportamento di Help Viewer usando un file pkgdef

1. Creare un file *con estensione pkgdef* con la prima riga come `[$RootKey$\Help]` .

2. Aggiungere uno o tutti i valori delle chiavi del Registro di sistema descritti nella tabella seguente su righe separate, ad esempio `"UseOnlineHelp"=dword:00000001`.

3. Copiare il file in *%ProgramFiles(x86)%\Microsoft Visual Studio\2017 \\<edition \> \Common7\IDE\CommonExtensions*.

4. Eseguire `devenv /updateconfiguration` in un prompt dei comandi per gli sviluppatori.

### <a name="registry-key-values"></a>Valori delle chiavi del Registro di sistema

|Valore della chiave del Registro di sistema|Tipo|Dati|Descrizione|
|------------------|----|----|-----------|
|NewContentAndUpdateService|string|\<http URL for service endpoint\>|Definire un endpoint di servizio univoco|
|UseOnlineHelp|dword|`0` per specificare la Guida locale, `1` per specificare la Guida online|Impostare la Guida online o offline come predefinita|
|OnlineBaseUrl|string|\<http URL for service endpoint\>|Definire un endpoint F1 univoco|
|OnlineHelpPreferenceDisabled|dword|`0` per abilitare o `1` per disabilitare l'opzione di preferenza della Guida online|Disabilitare l'opzione di preferenza della Guida online|
|DisableManageContent|dword|`0` per abilitare o `1` per disabilitare la scheda **Gestisci contenuto** in Help Viewer|Disabilitare la scheda **Gestisci contenuto**|
|DisableFirstRunHelpSelection|dword|`0` per abilitare o `1` per disabilitare le funzionalità della Guida configurate al primo avvio di Visual Studio|Disabilitare l'installazione del contenuto al primo avvio di Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Esempio di contenuto del file pkgdef

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Uso dell'editor del Registro di sistema per modificare il comportamento di Help Viewer

È possibile controllare i due comportamenti seguenti impostando i valori di chiavi del Registro di sistema nell'Editor del Registro di sistema.

|Attività|Chiave del Registro di sistema|Valore|Dati|
|----------|-----|------|----|
|Eseguire l'override della priorità del processo BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (in un computer a 64 bit)\Microsoft\Help\v2.3|BITSPriority|**foreground**, **high**, **normal** o **low**|
|Puntare all'archivio del contenuto locale nella condivisione di rete|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Vedi anche

- [Guida dell'amministratore di Help Viewer](../help-viewer/administrator-guide.md)
- [Argomenti della riga di comando per Gestione contenuto della Guida](../help-viewer/command-line-arguments.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)