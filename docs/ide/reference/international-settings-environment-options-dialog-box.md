---
title: Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86201db5cb71e7595cbfde82f04bcbb74ba149f2
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389630"
---
# <a name="international-settings-environment-options-dialog-box"></a>Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni

La pagina Impostazioni internazionali consente di modificare la lingua predefinita quando ci sono più versioni in lingue diverse dell'IDE (Integrated Development Environment) installato sul proprio computer. È possibile accedere a questa finestra di dialogo selezionando **Opzioni** dal menu **Strumenti** e scegliendo **Impostazioni internazionali** dalla cartella **Ambiente**. Se questa pagina non viene visualizzata nell'elenco, selezionare **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.

**Lingua**

Elenca le lingue disponibili per le versioni di lingua del prodotto installato. Questa opzione non è disponibile a meno che non vi siano più versioni di lingua installate sul proprio computer. Se l'ambiente è condiviso da più lingue di prodotti o da un'installazione mista di lingue dei prodotti, la selezione della lingua viene modificata in **Come Microsoft Windows**.

> [!CAUTION]
> In un sistema con più lingue installate, gli strumenti di compilazione Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e file correlati) non sono interessati da questa impostazione. Questi strumenti usano la versione dell'ultima lingua installata. Gli strumenti di compilazione per la lingua precedentemente installata vengono sovrascritti perché gli strumenti di compilazione di Visual C++ non usano il modello DLL satellite.

## <a name="see-also"></a>Vedere anche

- [Installare i Language Pack](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
- [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)