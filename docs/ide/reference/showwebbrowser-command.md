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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14e2d6f2c753c56d1628d20e921b7dff2aa83471
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926018"
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

## <a name="switches"></a>Opzioni
/new

facoltativo. Specifica che la pagina viene visualizzata in una nuova istanza del Web browser.

/ext

facoltativo. Specifica che la pagina viene visualizzata nel Web browser predefinito all'esterno dell'IDE.

## <a name="remarks"></a>Osservazioni
L'alias per il comando **ShowWebBrowser** è **navigate** o **nav**.

## <a name="example"></a>Esempio
L'esempio seguente illustra la home page di Microsoft Docs in un Web browser all'esterno dell'IDE. Se è già aperta un'istanza del Web browser, viene usata; in caso contrario, viene avviata una nuova istanza.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)