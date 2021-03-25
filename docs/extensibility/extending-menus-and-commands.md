---
title: Estensione di menu e comandi | Microsoft Docs
description: Informazioni sui comandi che aggiungono azioni e processi a Visual Studio. Il modello di progetto VSPackage Mostra come implementare un comando di base.
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
ms.workload:
- vssdk
ms.openlocfilehash: 6a96978cdad45c669b607c18e12b2e492dcf95bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075211"
---
# <a name="extend-menus-and-commands"></a>Estendi menu e comandi
I comandi sono il modo in cui si aggiungono azioni e processi a Visual Studio. Nella maggior parte dei casi i comandi vengono visualizzati nei menu o nelle barre degli strumenti. Il modello di progetto VSPackage Mostra come implementare un comando di base. Per un'implementazione leggermente più lunga ma ancora di base, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

 Per ulteriori informazioni sui comandi, i menu e le barre degli strumenti di Visual Studio, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

 I comandi, i menu e le barre degli strumenti sono definiti nel file con *estensione vsct* che fa parte dei progetti VSPackage. Per informazioni sull'IDE di Visual Studio e sul file con *estensione vsct* , vedere la pagina relativa all' [aggiunta di elementi dell'interfaccia utente da VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Negli argomenti seguenti viene illustrato come aggiungere diversi tipi di comandi, menu e barre degli strumenti.

## <a name="in-this-section"></a>Contenuto della sezione
- [Aggiungere un menu alla barra dei menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Viene illustrato come aggiungere un menu alla barra dei menu superiore di Visual Studio.

- [Associa scelte rapide da tastiera a voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Viene illustrato come aggiungere un tasto di scelta rapida (ad esempio CTRL + 3) a una voce di menu.

- [Aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md) Viene illustrato come aggiungere un sottomenu al menu principale.

- [Aggiungere un elenco usato più di recente a un sottomenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Viene illustrato come aggiungere un elenco di uso più recente.

- [Creare gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md) Viene descritto come raggruppare gli elementi del comando in modo che possano essere inclusi in più menu.

- [Aggiungere icone ai comandi di menu](../extensibility/adding-icons-to-menu-commands.md) Viene descritto come aggiungere un'icona a un comando sia in una barra degli strumenti che in un menu.

- [Modificare il testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md) Descrive l'uso del `TextChanges` flag per abilitare la modifica dinamica di una voce di menu.

- [Modificare l'aspetto di un comando](../extensibility/changing-the-appearance-of-a-command.md) Viene descritto come abilitare o disabilitare dinamicamente un comando.

- [Aggiornare l'interfaccia utente](../extensibility/updating-the-user-interface.md) Viene descritto come forzare un aggiornamento dell'interfaccia utente in modo da riflettere le modifiche recenti.

- [Comandi di menu Localize](../extensibility/localizing-menu-commands.md) Viene illustrato come localizzare i comandi di menu.
