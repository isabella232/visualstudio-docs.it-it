---
title: Linee guida per il posizionamento dei comandi | Microsoft Docs
description: Informazioni sulle linee guida e sulle procedure consigliate per il posizionamento dei comandi nell Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f0e78221b93d766b8dd0f018501f3fc808a98c16
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029008"
---
# <a name="command-placement-guidelines"></a>Linee guida per il posizionamento dei comandi
Le procedure consigliate per il posizionamento dei comandi nell Visual Studio'ambiente di sviluppo integrato (IDE) variano a seconda delle dimensioni del set di comandi. I comandi vengono definiti e posizionati in base alle informazioni nei *file con estensione vsct.*

## <a name="best-practices-for-all-command-sets"></a>Procedure consigliate per tutti i set di comandi
 Per ogni set di comandi, seguire queste linee guida:

- Preparare in anticipo un grafico della struttura dei comandi. Identificare i comandi, le caselle combinate, i gruppi di comandi e i menu di scelta rapida che verranno usati in più di una posizione.

- I comandi visualizzati nello stesso gruppo devono essere correlati.

- I gruppi che contengono un solo comando sono accettabili.

- I pacchetti non devono aggiungere molti comandi ai menu Visual Studio esistenti. Devono invece creare menu o sottomenu per ospitare i nuovi comandi.

- Quando si mette un comando in un menu esistente, assegnare un nome al comando in modo che lo scopo sia chiaro e non sia confuso con i comandi esistenti.

## <a name="best-practices-for-small-command-sets"></a>Procedure consigliate per set di comandi di piccole dimensioni
 Se si sviluppa un VSPackage con pochi comandi, seguire anche queste linee guida:

- Quando possibile, usare [l'elemento Parent](../../extensibility/parent-element.md) di un comando, una casella combinata, un gruppo o un menu figlio per inserire l'elemento nel gruppo appropriato.

- Assegnare questi gruppi ai menu visualizzati dal pacchetto VSPackage.

- L'elemento padre di un menu figlio o di un comando deve essere un [elemento Group.](../../extensibility/group-element.md) Assegnare comandi e menu figlio ai gruppi e quindi assegnare i gruppi ai menu padre.

- È possibile inserire un comando in gruppi aggiuntivi aggiungendo una sezione dell'elemento [CommandPlacements](../../extensibility/commandplacements-element.md) dopo la definizione del comando e quindi aggiungendo all'elemento un `CommandPlacements` [elemento CommandPlacement](../../extensibility/commandplacement-element.md) per ogni gruppo aggiuntivo.

## <a name="best-practices-for-large-command-sets"></a>Procedure consigliate per set di comandi di grandi dimensioni
 Se il vspackage avrà molti comandi che verranno visualizzati in più contesti, seguire anche queste linee guida:

- Creare menu, gruppi e comandi auto-padre. Ciò significa che non assegnare un `Parent` elemento nella definizione dell'elemento.

- Usare `CommandPlacement` le voci degli elementi nella sezione dell'elemento per inserire menu, gruppi e comandi nei `CommandPlacements` relativi menu e gruppi padre.

- Nella sezione `CommandPlacements` dell'elemento le voci che popolano un determinato menu o gruppo devono essere adiacenti tra loro. Ciò facilita la leggibilità e semplifica `Priority` la determinazione delle classificazioni.

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
