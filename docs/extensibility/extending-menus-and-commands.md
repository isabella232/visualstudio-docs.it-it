---
title: Estensione di menu e comandi Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711804"
---
# <a name="extend-menus-and-commands"></a>Estendere menu e comandi
I comandi sono il modo in cui si aggiungono azioni e processi a Visual Studio.Commands are the way you add actions and processes to Visual Studio. Nella maggior parte dei casi i comandi vengono visualizzati nei menu o nelle barre degli strumenti. Il modello di progetto VSPackage viene illustrato come implementare un comando molto semplice. Per un'implementazione leggermente più lunga ma ancora di base, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu.

 Per ulteriori informazioni sui comandi, i menu e le barre degli strumenti di Visual Studio, vedere [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

 Comandi, menu e barre degli strumenti sono definiti nel file *vsct* che fa parte dei progetti VSPackage. È possibile trovare informazioni sull'IDE di Visual Studio e il file *vsct* in [come VSPackage aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Negli argomenti seguenti viene illustrato come aggiungere diversi tipi di comandi, menu e barre degli strumenti.

## <a name="in-this-section"></a>Contenuto della sezione
- Aggiungere un menu alla barra dei menu di [Visual StudioAdd a menu to the Visual Studio menu bar](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Viene illustrato come aggiungere un menu alla barra dei menu di Visual Studio superiore.

- [Associare i tasti di scelta rapida alle voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Viene illustrato come aggiungere una scelta rapida da tastiera (ad esempio CTRL e 3) a una voce di menu.

- [Aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md) Viene illustrato come aggiungere un sottomenu al menu superiore.

- [Aggiungere un elenco usato più di recente a un sottomenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Viene illustrato come aggiungere un elenco Usati più di recente.

- [Creare gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md) Viene descritto come raggruppare gli elementi di comando in modo che possano essere inclusi in più menu.

- [Aggiungere icone ai comandi di menu](../extensibility/adding-icons-to-menu-commands.md) Viene descritto come aggiungere un'icona a un comando sia su una barra degli strumenti che su un menu.

- [Modificare il testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md) Viene descritto l'utilizzo del flag per consentire la `TextChanges` modifica dinamica di una voce di menu.

- [Modificare l'aspetto di un comando](../extensibility/changing-the-appearance-of-a-command.md) Viene descritto come abilitare o disabilitare dinamicamente un comando.

- [Aggiornare l'interfaccia utente](../extensibility/updating-the-user-interface.md) Viene descritto come forzare un aggiornamento dell'interfaccia utente per riflettere le modifiche recenti.

- [Localizzare i comandi di menu](../extensibility/localizing-menu-commands.md) Viene illustrato come localizzare i comandi di menu.
