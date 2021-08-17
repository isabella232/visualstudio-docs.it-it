---
title: Estensione di menu e comandi | Microsoft Docs
description: Informazioni sui comandi, che aggiungono azioni e processi Visual Studio. Il modello di progetto VSPackage illustra come implementare un comando di base.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a9b7070b491b56c0a99e3fc6a06e4d64b0f7d4c20834fdd1a069c9b54a267deb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448377"
---
# <a name="extend-menus-and-commands"></a>Estendere menu e comandi
I comandi sono il modo in cui si aggiungono azioni e processi Visual Studio. Nella maggior parte dei casi i comandi vengono visualizzati nei menu o nelle barre degli strumenti. Il modello di progetto VSPackage illustra come implementare un comando di base. Per un'implementazione leggermente più lunga ma ancora di base, vedere [Creare un'estensione con un comando di menu.](../extensibility/creating-an-extension-with-a-menu-command.md)

 Per altre informazioni su Visual Studio comandi, menu e barre degli strumenti, vedere [Comandi, menu e barre degli strumenti.](../extensibility/internals/commands-menus-and-toolbars.md)

 Comandi, menu e barre degli strumenti sono definiti nel file con estensione *vsct* che fa parte di progetti VSPackage. È possibile trovare informazioni sull'IDE Visual Studio e sul file con estensione *vsct* in Come i pacchetti VSPackage aggiungono [elementi dell'interfaccia utente.](../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Negli argomenti seguenti viene illustrato come aggiungere diversi tipi di comandi, menu e barre degli strumenti.

## <a name="in-this-section"></a>Contenuto della sezione
- [Aggiungere un menu alla barra Visual Studio menu](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Illustra come aggiungere un menu alla barra dei menu Visual Studio superiore.

- [Associare i tasti di scelta rapida alle voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Illustra come aggiungere un tasto di scelta rapida (ad esempio CTRL+3) a una voce di menu.

- [Aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md) Illustra come aggiungere un sottomenu al menu in alto.

- [Aggiungere un elenco usato più di recente a un sottomenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Viene illustrato come aggiungere un elenco degli elementi usati più di recente.

- [Creare gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md) Viene descritto come raggruppare gli elementi di comando in modo che possano essere inclusi in più menu.

- [Aggiungere icone ai comandi di menu](../extensibility/adding-icons-to-menu-commands.md) Descrive come aggiungere un'icona a un comando sia in una barra degli strumenti che in un menu.

- [Modificare il testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md) Viene descritto l'utilizzo del flag per consentire la modifica dinamica `TextChanges` di una voce di menu.

- [Modificare l'aspetto di un comando](../extensibility/changing-the-appearance-of-a-command.md) Viene descritto come abilitare o disabilitare dinamicamente un comando.

- [Aggiornare l'interfaccia utente](../extensibility/updating-the-user-interface.md) Viene descritto come forzare un aggiornamento dell'interfaccia utente per riflettere le modifiche recenti.

- [Comandi di menu Localizza](../extensibility/localizing-menu-commands.md) Viene illustrato come localizzare i comandi di menu.
