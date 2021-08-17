---
title: 'Procedura: Identificare i simboli in una libreria | Microsoft Docs'
description: Informazioni su come identificare i simboli in una libreria implementando metodi che passano le informazioni di navigazione dalla libreria di simboli al gestore Visual Studio oggetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 33000a513f4a2580bb74a0b6ed5267231739244c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042504"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Procedura: Identificare i simboli in una libreria
Gli strumenti di esplorazione dei simboli visualizzano le visualizzazioni gerarchiche dei simboli. I simboli rappresentano spazi dei nomi, oggetti, classi, membri di classe e altri elementi del linguaggio.

 Ogni simbolo nella gerarchia può essere identificato dalle informazioni di navigazione passate dalla libreria di simboli al gestore oggetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite le interfacce seguenti:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 La posizione del simbolo nella gerarchia distingue un simbolo. Consente agli strumenti di esplorazione dei simboli di passare a un simbolo specifico. Il percorso univoco completo del simbolo determina la posizione. Ogni elemento nel percorso è un nodo. Il percorso inizia con il nodo di primo livello e termina con il simbolo specifico. Ad esempio, se il metodo M1 è un membro della classe C1 e C1 si trova nello spazio dei nomi N1, il percorso completo del metodo M1 è N1. C1. M1. Questo percorso contiene tre nodi: N1, C1 e M1.

 Le informazioni di navigazione consentono al gestore oggetti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] individuare, selezionare e mantenere selezionati i simboli nella gerarchia. Consente di spostarsi da uno strumento di esplorazione a un altro. Quando si **usa Visualizzatore** oggetti per esplorare i simboli in un progetto, è possibile fare clic con il pulsante destro del mouse su un metodo e avviare lo strumento Visualizzatore chiamate per visualizzare il metodo in un grafico [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]  chiamate.

 Due forme descrivono la posizione del simbolo. Il formato canonico è basato sul percorso completo del simbolo. Rappresenta una posizione univoca del simbolo nella gerarchia. È indipendente dello strumento di esplorazione dei simboli. Per ottenere le informazioni sul modulo canonico, il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore oggetti chiama il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> . Il modulo di presentazione descrive la posizione del simbolo all'interno di uno strumento di esplorazione dei simboli specifico. La posizione del simbolo è relativa alla posizione di altri simboli nella gerarchia. Un determinato simbolo può avere diversi percorsi di presentazione, ma solo un percorso canonico. Ad esempio, se la classe C1 viene ereditata dalla classe C2 ed entrambe le classi si trova nello spazio dei nomi N1, nel **Visualizzatore** oggetti viene visualizzato l'albero gerarchico seguente:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Il percorso canonico della classe C2, in questo esempio, è N1 + C2. Il percorso di presentazione di C2 include nodi C1 e "Basi e interfacce": N1 + C1 + "Basi e interfacce" + C2.

 Per ottenere le informazioni sul modulo di presentazione, il gestore oggetti chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> il metodo .

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Per ottenere informazioni sui moduli canonici e di presentazione

1. Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.

     Il gestore oggetti chiama questo metodo per ottenere l'elenco di nodi contenuti nel percorso canonico del simbolo.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.

     Il gestore oggetti chiama questo metodo per ottenere l'elenco di nodi contenuti nel percorso di presentazione del simbolo.

## <a name="see-also"></a>Vedi anche
- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Procedura: Registrare una libreria con gestione oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Procedura: Esporre gli elenchi di simboli forniti dalla libreria al gestore oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
