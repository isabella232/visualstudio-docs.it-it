---
title: Estensione di menu e comandi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 158759d2511b6ba1209a045a898969fce774e0a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520264"
---
# <a name="extending-menus-and-commands"></a>Estensione di menu e comandi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [estensione di menu e comandi](https://docs.microsoft.com/visualstudio/extensibility/extending-menus-and-commands).  
  
I comandi sono la procedura per aggiungere azioni e i processi per Visual Studio. Nella maggior parte dei casi i comandi vengono visualizzati nei menu o barre degli strumenti. Il modello di progetto VSPackage viene illustrato come implementare un comando molto semplice. Per un'implementazione leggermente più lunga, ma comunque fondamentale, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Per altre informazioni sui comandi, menu e barre degli strumenti di Visual Studio, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 I comandi, menu e barre degli strumenti sono definiti nel file vsct che fa parte di progetti VSPackage. È possibile trovare informazioni sull'IDE di Visual Studio e il file con estensione vsct [modo in cui i pacchetti VSPackage aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Gli argomenti seguenti illustrano come aggiungere diversi tipi di comandi, menu e barre degli strumenti.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Aggiunta di un menu alla barra dei menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Viene illustrato come aggiungere un menu all'inizio barra dei menu di Visual Studio.  
  
 [Associazione di scelte rapide da tastiera a voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Viene illustrato come aggiungere un tasto di scelta rapida (ad esempio, CTRL + 3) per una voce di menu.  
  
 [Aggiunta di un sottomenu a un menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Viene illustrato come aggiungere un sottomenu al menu in alto.  
  
 [Aggiunta di un elenco usato più di recente a un sottomenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Viene illustrato come aggiungere un elenco usati di recente.  
  
 [Creazione di gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md)  
 Viene descritto come raggruppare gli elementi di comando in modo che possono essere incluse nel menu multipli.  
  
 [Aggiunta di icone ai comandi di menu](../extensibility/adding-icons-to-menu-commands.md)  
 Viene descritto come aggiungere un'icona per un comando su una barra degli strumenti sia un menu.  
  
 [Modifica del testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Viene descritto come utilizzare il `TextChanges` flag per abilitare una voce di menu essere modificato in modo dinamico.  
  
 [Modifica dell'aspetto di un comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Viene descritto come abilitare o disabilitare un comando in modo dinamico.  
  
 [Aggiornamento dell'interfaccia utente](../extensibility/updating-the-user-interface.md)  
 Viene descritto come forzare un aggiornamento dell'interfaccia utente in modo da riflettere le modifiche recenti.  
  
 [Localizzazione dei comandi di menu](../extensibility/localizing-menu-commands.md)  
 Viene illustrato come localizzare i comandi di menu.  
  
## <a name="related-sections"></a>Sezioni correlate
