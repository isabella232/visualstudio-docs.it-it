---
title: Comando ShowWebBrowser
description: Informazioni sul comando Mostra Web Browser e su come viene visualizzato l'URL specificato in una finestra del Web browser all'interno dell'IDE o esterno all'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 66da9ebb378d16bb73910ed2b84e379ab5bfaa2c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150976"
---
# <a name="showwebbrowser-command"></a>Comando ShowWebBrowser

Visualizza l'URL specificato in una finestra del Web browser all'interno o all'esterno dell'ambiente di sviluppo integrato (IDE).

## <a name="syntax"></a>Sintassi

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argomenti
`URL`

Obbligatorio. URL (Uniform Resource Locator) per il sito Web.

## <a name="switches"></a>Commutatori
/new

facoltativo. Specifica che la pagina viene visualizzata in una nuova istanza del Web browser.

/ext

facoltativo. Specifica che la pagina viene visualizzata nel Web browser predefinito all'esterno dell'IDE.

## <a name="remarks"></a>Commenti
L'alias per il comando **ShowWebBrowser** è **navigate** o **nav**.

## <a name="example"></a>Esempio
L'esempio seguente illustra la home page di Microsoft Docs in un Web browser all'esterno dell'IDE. Se è già aperta un'istanza del Web browser, viene usata; in caso contrario, viene avviata una nuova istanza.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Vedi anche

- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella di ricerca/comando](../../ide/find-command-box.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)