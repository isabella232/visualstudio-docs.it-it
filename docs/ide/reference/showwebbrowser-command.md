---
title: Comando ShowWebBrowser
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8c97659cc6036433c5bcf2547a9f88aee56f451
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747720"
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

## <a name="switches"></a>Switch
/new

Facoltativa. Specifica che la pagina viene visualizzata in una nuova istanza del Web browser.

/ext

Facoltativa. Specifica che la pagina viene visualizzata nel Web browser predefinito all'esterno dell'IDE.

## <a name="remarks"></a>Osservazioni
L'alias per il comando **ShowWebBrowser** è **navigate** o **nav**.

## <a name="example"></a>Esempio
L'esempio seguente illustra la home page di Microsoft Docs in un Web browser all'esterno dell'IDE. Se è già aperta un'istanza del Web browser, viene usata; in caso contrario, viene avviata una nuova istanza.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Vedere anche

- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) (Comandi di Visual Studio)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)