---
title: -LCID (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac74f5275288cdba35d3a70f4a7813c800e4327d
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704720"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Imposta la lingua predefinita usata per il testo, la valuta e altri valori all'interno dell'ambiente di sviluppo integrato (IDE).

## <a name="syntax"></a>Sintassi

```cmd
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Argomenti
 `LocaleID` Obbligatorio. LCID (ID impostazioni locali) della lingua specificata.

## <a name="remarks"></a>Note
 Carica l'IDE e imposta la lingua naturale predefinita per l'ambiente. Questa modifica è persistente tra le sessioni e viene riportata nel riquadro **Impostazioni internazionali** delle opzioni **Ambiente** nella finestra di dialogo **Opzioni** nell'IDE.

 Se la lingua specificata non è disponibile nel sistema dell'utente, l'opzione /LCID viene ignorata.

 Nella tabella seguente vengono elencati gli LCID delle lingue supportate da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Linguaggio|LCID|
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

```cmd
devenv /LCID 1033
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)