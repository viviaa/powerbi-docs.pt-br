---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193491"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Usando a função DAX username() ou userprincipalname()
Você pode tirar proveito das funções DAX *username()* ou *userprincipalname()* dentro de seu conjunto de dados. Você pode usá-las dentro de expressões no Power BI Desktop. Quando você publicar seu modelo, ele será usado no serviço do Power BI.

No Power BI Desktop, *username()* retorna um usuário no formato *DOMÍNIO\Usuário* e *userprincipalname()* retorna um usuário no formato <em>user@contoso.com</em>.

No serviço do Power BI, *username()* e *userprincipalname()* retornam o nome UPN do usuário. Isso se parece com um endereço de email.

