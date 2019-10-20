---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 991886289ac2c2ee06e37476169dff6d2354a52e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659988"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Imposta la lingua predefinita usata per testo, valuta e altri valori all'interno dell'IDE.

## <a name="syntax"></a>Sintassi

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>argomenti

- *LocaleID*

  Obbligatorio. Identificatore delle impostazioni locali (LCID) della lingua specificata.

## <a name="remarks"></a>Note

Carica l'IDE e imposta la lingua naturale predefinita per l'ambiente. Questa modifica viene salvata tra le sessioni e l'IDE mostra la modifica nella casella **Strumenti** > **Opzioni** > **Ambiente** > **Impostazioni internazionali** > **Lingua**.

Se la lingua specificata non è disponibile nel sistema in uso, l'opzione `/LCID` viene ignorata.

Nella tabella seguente vengono elencati gli LCID delle lingue supportate da Visual Studio.

|Language|LCID|
|--------------|----------|
|Cinese (semplificato)|2052|
|Cinese (tradizionale)|1028|
|Inglese|1040|
|Francese|1036|
|Tedesco|1031|
|Italiano|1040|
|Giapponese|1041|
|Coreano|1042|
|Spagnolo|3082|

## <a name="example"></a>Esempio

In questo esempio viene caricato l'IDE con le stringhe delle risorse in lingua inglese.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)