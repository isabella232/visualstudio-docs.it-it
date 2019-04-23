---
title: Controllare gli aggiornamenti delle distribuzioni
description: Informazioni sulla procedura di modifica della posizione in cui Visual Studio cerca un aggiornamento durante l'installazione da una rete.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a58ee5350467ae2b2eea74b4f929fac69b75c071
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58856288"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio

In molti casi, gli amministratori aziendali creano un layout e lo inseriscono in una condivisione file di rete per poter essere distribuito agli utenti finali.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Controllo della posizione in cui Visual Studio cerca gli aggiornamenti

Per impostazione predefinita, Visual Studio continua a cercare gli aggiornamenti online anche se l'installazione è stata distribuita da una condivisione di rete. Se è disponibile un aggiornamento, l'utente può installarlo. Eventuali contenuti aggiornati non disponibili nel layout offline sono scaricati dal Web.

Per controllare direttamente le posizioni in cui Visual Studio cerca gli aggiornamenti, è possibile modificare il percorso in cui avviene la ricerca. È inoltre possibile controllare la versione dell’aggiornamento degli utenti. A tale scopo, attenersi alla seguente procedura:

1. Creare un layout offline:
   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```
2. Copiarlo nella condivisione file in cui si vuole inserirlo:
   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```
3. Modificare il file response.json nel layout e cambiare il valore `channelUri` in modo che punti a una copia del file channelManifest.json controllato dall'amministratore.

   Assicurarsi di usare le barre rovesciate come carattere di escape nel valore, come illustrato nell’esempio seguente:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Gli utenti finali possono ora eseguire l'installazione da questa condivisione per installare Visual Studio.
   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Quando un amministratore aziendale stabilisce che per gli utenti finali è il momento di eseguire l'aggiornamento a una versione più recente di Visual Studio, è possibile [aggiornare la posizione di layout](update-a-network-installation-of-visual-studio.md) in cui incorporare i file aggiornati, come segue.

1. Utilizzare un comando simile a quello che segue:
   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```
2. Verificare che il file response.json nel layout aggiornato contenga ancora le personalizzazioni, in particolare la modifica del valore channelUri, come segue:
   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```
   Le installazioni esistenti di Visual Studio da questo layout eseguono la ricerca degli aggiornamenti in `\\server\share\VS\ChannelManifest.json`. Se il file channelManifest.json è più recente rispetto a quello installato dall'utente, Visual Studio informerà l'utente che è disponibile un aggiornamento.

   Le nuove installazioni installano automaticamente la versione aggiornata di Visual Studio direttamente dal layout.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Controllo delle notifiche nell'IDE di Visual Studio

::: moniker range="vs-2017"

Come descritto in precedenza, Visual Studio controlla l'eventuale presenza di aggiornamenti nel percorso da cui è stato installato (ad esempio, la condivisione di rete o Internet). Se è disponibile un aggiornamento, Visual Studio ne informa l'utente con un flag di notifica nell'angolo superiore destro della finestra.

   ![Flag di notifica per gli aggiornamenti](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Come descritto in precedenza, Visual Studio controlla l'eventuale presenza di aggiornamenti nel percorso da cui è stato installato (ad esempio, la condivisione di rete o Internet). Se è disponibile un aggiornamento, Visual Studio ne informa l'utente con un'icona di notifica nell'angolo inferiore destro della finestra.

   ![Icona di notifica nell'IDE di Visual Studio](media/vs-2019/notification-bar.png "Icona di notifica nell'IDE di Visual Studio")

::: moniker-end

Se si preferisce non informare gli utenti della disponibilità di aggiornamenti, è possibile disabilitare le notifiche. Ad esempio, se si distribuiscono gli aggiornamenti attraverso un meccanismo di distribuzione centrale del software, è possibile voler disabilitare queste notifiche.

::: moniker range="vs-2017"

Poiché Visual Studio 2017 [archivia le voci del Registro di sistema in un registro privato](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), non è possibile modificare direttamente il Registro di sistema nel modo consueto. Visual Studio include, tuttavia, un’utility `vsregedit.exe` che consente di modificare le impostazioni di Visual Studio. È possibile disattivare le notifiche con il comando seguente:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```
::: moniker-end

::: moniker range="vs-2019"

Poiché Visual Studio 2019 [archivia le voci del Registro di sistema in un registro privato](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), non è possibile modificare direttamente il Registro di sistema nel modo consueto. Visual Studio include, tuttavia, un’utility `vsregedit.exe` che consente di modificare le impostazioni di Visual Studio. È possibile disattivare le notifiche con il comando seguente:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

Accertarsi di sostituire la directory in modo che coincida con l'istanza installata che si vuole modificare.

> [!TIP]
> Usare [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) per trovare un'istanza specifica di Visual Studio in una workstation client.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
