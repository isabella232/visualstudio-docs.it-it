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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e55c0e81877c2735571705a2b2d2529b0fa3a74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666999"
---
# <a name="options-dialog-box-environment--international-settings"></a>Finestra di dialogo Opzioni: ambiente \> impostazioni internazionali

La pagina Impostazioni internazionali consente di modificare la lingua predefinita quando nel computer in uso sono installate più versioni in lingue diverse dell'IDE (Integrated Development Environment). È possibile accedere a questa finestra di dialogo selezionando **Opzioni** dal menu **Strumenti** e scegliendo **Impostazioni internazionali** dalla cartella **Ambiente**.

**Linguaggio**

Elenca le lingue disponibili per le versioni di lingua del prodotto installato. Se l'ambiente è condiviso da più lingue di prodotti o da un'installazione mista di lingue dei prodotti, la selezione della lingua viene modificata in **Come Microsoft Windows**.

> [!CAUTION]
> In un sistema con più lingue installate, gli strumenti di compilazione Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e file correlati) non sono interessati da questa impostazione. Questi strumenti usano la versione dell'ultima lingua installata. Gli strumenti di compilazione per la lingua precedentemente installata vengono sovrascritti perché gli strumenti di compilazione di Visual C++ non usano il modello DLL satellite.

### <a name="see-also"></a>Vedere anche

- [Installare i Language Pack](../../install/install-visual-studio.md#step-6---install-language-packs-optional)