---
title: Estensione di menu e comandi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ef32dd2bbc44f784a2faaf6edcafcba96a8f113
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910490"
---
# <a name="extend-menus-and-commands"></a>Estendere i menu e comandi
I comandi sono la procedura per aggiungere azioni e i processi per Visual Studio. Nella maggior parte dei casi i comandi vengono visualizzati nei menu o barre degli strumenti. Il modello di progetto VSPackage viene illustrato come implementare un comando molto semplice. Per un'implementazione leggermente più lunga, ma comunque fondamentale, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Per altre informazioni sui comandi, menu e barre degli strumenti di Visual Studio, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 I comandi, menu e barre degli strumenti sono definiti nel *vsct* file che è parte di progetti di VSPackage. È possibile trovare informazioni sull'IDE di Visual Studio e il *vsct* del file in [modo in cui i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Gli argomenti seguenti illustrano come aggiungere diversi tipi di comandi, menu e barre degli strumenti.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Aggiungere un menu alla barra dei menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Viene illustrato come aggiungere un menu all'inizio barra dei menu di Visual Studio.  
  
 [Eseguire l'associazione di scelte rapide da tastiera a voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Viene illustrato come aggiungere un tasto di scelta rapida (ad esempio, CTRL + 3) per una voce di menu.  
  
 [Aggiungere un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Viene illustrato come aggiungere un sottomenu al menu in alto.  
  
 [Aggiungere che un usati di recente elenco a un sottomenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Viene illustrato come aggiungere un elenco usati di recente.  
  
 [Creazione di gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md)  
 Viene descritto come raggruppare gli elementi di comando in modo che possono essere incluse nel menu multipli.  
  
 [Aggiungere le icone ai comandi di menu](../extensibility/adding-icons-to-menu-commands.md)  
 Viene descritto come aggiungere un'icona per un comando su una barra degli strumenti sia un menu.  
  
 [Modificare il testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Viene descritto come utilizzare il `TextChanges` flag per abilitare una voce di menu essere modificato in modo dinamico.  
  
 [Modificare l'aspetto di un comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Viene descritto come abilitare o disabilitare un comando in modo dinamico.  
  
 [Aggiornare l'interfaccia utente](../extensibility/updating-the-user-interface.md)  
 Viene descritto come forzare un aggiornamento dell'interfaccia utente in modo da riflettere le modifiche recenti.  
  
 [Localizzare i comandi di menu](../extensibility/localizing-menu-commands.md)  
 Viene illustrato come localizzare i comandi di menu.  