---
title: Estensione di progetti | Microsoft Docs
description: Informazioni su come creare tipi di progetto personalizzati in Visual Studio SDK e su come gestire i diversi tipi di soluzioni di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 997f4e32007af641b24ba933d2c891e447382786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895830"
---
# <a name="extend-projects"></a>Estendi progetti
I progetti e le soluzioni sono i modi in cui Visual Studio organizza i file di codice e di risorse nelle unità di compilazione e distribuzione. È possibile trovare altre informazioni sui progetti in [progetti (Visual Studio SDK)](../extensibility/extending-projects.md).

 È possibile creare tipi di progetto personalizzati con Visual Studio SDK e il Framework di pacchetto gestito per i progetti, che è possibile scaricare nel [Framework di pacchetto gestito per i progetti](https://github.com/tunnelvisionlabs/MPFProj10). Per comprendere come vengono implementati i progetti personalizzati, vedere [creazione di un nuovo progetto: dietro le quinte, parte 1](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nuova generazione di progetti: dietro le quinte, parte 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Negli argomenti di questa sezione viene descritto come creare progetti personalizzati e come gestire tipi diversi di soluzioni di Visual Studio.

## <a name="in-this-section"></a>Contenuto della sezione
- [Creazione di un sistema di progetto di base, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) Viene descritto come creare un sistema di progetto personalizzato.

- [Creazione di un sistema di progetto di base, parte 2](../extensibility/creating-a-basic-project-system-part-2.md) Viene descritto come creare un sistema di progetto personalizzato.

- [Salvare i dati nei file di progetto](../extensibility/saving-data-in-project-files.md) Viene illustrato come aggiungere al progetto (<em>.</em> file proj *).

- [Verificare i sottotipi di un progetto in fase di esecuzione](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Viene illustrato come verificare il sottotipo di un progetto in fase di esecuzione.

- [Aggiungere e rimuovere pagine delle proprietà](../extensibility/adding-and-removing-property-pages.md) Viene illustrato come personalizzare le pagine delle proprietà per il progetto personalizzato.

- [Aggiungere un attributo a un elemento di progetto](../extensibility/adding-an-attribute-to-a-project-item.md) Viene illustrato come aggiungere un attributo a un elemento di progetto personalizzato.

- Rende [permanente la proprietà di un elemento di progetto](../extensibility/persisting-the-property-of-a-project-item.md) Viene illustrato come salvare in modo permanente le proprietà di un elemento di progetto personalizzato.

- [Gestire i progetti di Windows universale](../extensibility/managing-universal-windows-projects.md) Viene illustrato come gestire i progetti universali.
