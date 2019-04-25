---
title: Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64e65894fffd9c6786c19a337fc386f45fb9d203
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540667"
---
# <a name="options-dialog-box-environment--international-settings"></a>Finestra di dialogo Opzioni: Ambiente \> Impostazioni internazionali

La pagina Impostazioni internazionali consente di modificare la lingua predefinita quando nel computer in uso sono installate più versioni in lingue diverse dell'IDE (Integrated Development Environment). È possibile accedere a questa finestra di dialogo selezionando **Opzioni** dal menu **Strumenti** e scegliendo **Impostazioni internazionali** dalla cartella **Ambiente**.

**Lingua**

Elenca le lingue disponibili per le versioni di lingua del prodotto installato. Se l'ambiente è condiviso da più lingue di prodotti o da un'installazione mista di lingue dei prodotti, la selezione della lingua viene modificata in **Come Microsoft Windows**.

> [!CAUTION]
> In un sistema con più lingue installate, gli strumenti di compilazione Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e file correlati) non sono interessati da questa impostazione. Questi strumenti usano la versione dell'ultima lingua installata. Gli strumenti di compilazione per la lingua precedentemente installata vengono sovrascritti perché gli strumenti di compilazione di Visual C++ non usano il modello DLL satellite.

### <a name="see-also"></a>Vedere anche

- [Installare i Language Pack](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
- [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)