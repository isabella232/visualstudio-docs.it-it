---
title: Linee guida per il posizionamento dei comandi Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709561"
---
# <a name="command-placement-guidelines"></a>Linee guida per il posizionamento dei comandi
Le procedure consigliate per il posizionamento dei comandi nell'ambiente di sviluppo integrato (IDE) di Visual Studio variano a seconda delle dimensioni del set di comandi. I comandi vengono definiti e posizionati in base alle informazioni contenute nei file *vsct.*

## <a name="best-practices-for-all-command-sets"></a>Procedure consigliate per tutti i set di comandiBest practices for all command sets
 Per ogni set di comandi, seguire queste linee guida:For every set of commands, follow these guidelines:

- Preparare un grafico della struttura dei comandi in anticipo. Identificare i comandi, le caselle combinate, i gruppi di comandi e i menu di scelta rapida che verranno utilizzati in più posizioni.

- I comandi visualizzati nello stesso gruppo devono essere correlati.

- I gruppi che contengono un solo comando sono accettabili.

- I pacchetti non devono aggiungere molti comandi ai menu di Visual Studio esistenti. Al contrario, devono creare menu o sottomenu per ospitare i nuovi comandi.

- Quando si inserisce un comando in un menu esistente, assegnare un nome al comando in modo che lo scopo sia chiaro e non venga confuso con i comandi esistenti.

## <a name="best-practices-for-small-command-sets"></a>Procedure consigliate per set di comandi di piccole dimensioniBest practices for small command sets
 Se si sviluppa un pacchetto VSPackage che contiene solo alcuni comandi, seguire anche queste linee guida:If you are developing a VSPackage that has just a few commands, also follow these guidelines:

- Quando possibile, utilizzare l'elemento [Padre](../../extensibility/parent-element.md) di un comando, una casella combinata, un gruppo o un menu figlio per inserirlo nel gruppo appropriato.

- Assegnare questi gruppi ai menu visualizzati dal pacchetto VSPackage.Assign these groups to menus displayed by the VSPackage.

- L'elemento padre di un menu figlio o di un comando deve essere un elemento [Group.](../../extensibility/group-element.md) Assegnare comandi e menu figlio ai gruppi, quindi assegnare i gruppi ai menu padre.

- È possibile inserire un comando in gruppi aggiuntivi aggiungendo un [CommandPlacements](../../extensibility/commandplacements-element.md) sezione dell'elemento dopo la definizione del comando e quindi aggiungendo all'elemento `CommandPlacements` un [CommandPlacement](../../extensibility/commandplacement-element.md) elemento per ogni gruppo aggiuntivo.

## <a name="best-practices-for-large-command-sets"></a>Procedure consigliate per set di comandi di grandi dimensioniBest practices for large command sets
 Se il pacchetto VSPackage avrà molti comandi che verranno visualizzati in più contesti, seguire anche queste linee guida:If your VSPackage will have many commands that will appear in multiple contexts, also follow these guidelines:

- Rendere i menu, i gruppi e i comandi auto-genitori. Ovvero, non assegnare `Parent` un elemento nella definizione dell'elemento.

- Utilizzare `CommandPlacement` le voci `CommandPlacements` degli elementi nella sezione degli elementi per inserire menu, gruppi e comandi nei menu e nei gruppi padre.

- Nella `CommandPlacements` sezione dell'elemento, le voci che popolano un determinato menu o gruppo devono essere adiacenti l'una all'altra. Questo facilita la leggibilità e rende le `Priority` classifiche più facili da determinare.

## <a name="see-also"></a>Vedere anche
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
