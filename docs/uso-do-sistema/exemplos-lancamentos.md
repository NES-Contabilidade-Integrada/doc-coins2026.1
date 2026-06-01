# Manual de Instrução

Este manual apresenta três cenários de teste para o sistema: lucro, resultado neutro e prejuízo. Os exemplos utilizam contas do plano de contas do projeto, priorizando o nome da conta e o grupo, para facilitar a adaptação caso os códigos sejam alterados futuramente.

## Vídeo de demonstração

<div style="text-align:center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/u8mYq7SuCC4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

---

## Exemplos de lançamentos

=== "Lucro"

    ### Objetivo do teste

    Validar um cenário completo em que a empresa realiza vendas, registra custos, despesas, impostos, aplicação financeira e rendimento, encerrando o período com lucro.

    ### Lançamentos no Livro Diário

    | Nº | Data | Conta Débito | Grupo da Conta Débito | Conta Crédito | Grupo da Conta Crédito | Valor | Histórico |
    |----|------|-------------|----------------------|--------------|----------------------|-------|-----------|
    | 1 | 01/01/2026 | Banco A | Ativo | Capital Social | Patrimônio Líquido | R$ 100.000,00 | Integralização de capital social no Banco A. |
    | 2 | 05/01/2026 | Mercadorias para Revenda | Ativo | Fornecedor 1 | Passivo | R$ 40.000,00 | Compra de mercadorias para revenda a prazo. |
    | 3 | 08/01/2026 | Móveis e Utensílios | Ativo | Banco A | Ativo | R$ 12.000,00 | Compra de móveis e utensílios pagos pelo Banco A. |
    | 4 | 10/01/2026 | Cliente A | Ativo | Venda de Mercadorias | Contas de Resultado — Receitas | R$ 60.000,00 | Venda de mercadorias a prazo para o Cliente A. |
    | 5 | 10/01/2026 | Custos das Mercadorias Vendidas | Contas de Resultado — Custos e Despesas | Mercadorias para Revenda | Ativo | R$ 25.000,00 | Baixa do estoque pelo custo das mercadorias vendidas. |
    | 6 | 10/01/2026 | Simples Nacional | Contas de Resultado — Receitas / Deduções | Simples Nacional a Recolher | Passivo | R$ 5.000,00 | Reconhecimento de imposto sobre a venda de mercadorias. |
    | 7 | 15/01/2026 | Banco A | Ativo | Cliente A | Ativo | R$ 35.000,00 | Recebimento parcial do Cliente A no Banco A. |
    | 8 | 20/01/2026 | Salários e Ordenados e Encargos | Contas de Resultado — Custos e Despesas | Salários e Ordenados a Pagar | Passivo | R$ 8.000,00 | Apropriação de salários administrativos a pagar. |
    | 9 | 22/01/2026 | Energia Elétrica | Contas de Resultado — Custos e Despesas | Banco A | Ativo | R$ 1.500,00 | Pagamento de energia elétrica pelo Banco A. |
    | 10 | 25/01/2026 | Aplicações | Ativo | Banco A | Ativo | R$ 20.000,00 | Aplicação financeira realizada com recursos disponíveis no Banco A. |
    | 11 | 28/01/2026 | Fornecedor 1 | Passivo | Banco A | Ativo | R$ 15.000,00 | Pagamento parcial ao Fornecedor 1. |
    | 12 | 31/01/2026 | Banco A | Ativo | Juros de Aplicações | Contas de Resultado — Receitas | R$ 500,00 | Reconhecimento de rendimento de aplicação financeira. |

    ### Resultado esperado na apuração

    | Item | Valor esperado |
    |------|---------------|
    | Total de Receitas | R$ 60.500,00 |
    | Total de Custos e Despesas | R$ 34.500,00 |
    | Deduções da Receita | R$ 5.000,00 |
    | Resultado do Período | R$ 21.000,00 |
    | Tipo de Resultado | **Lucro** |

    A apuração deve demonstrar os lançamentos automáticos gerados em segundo plano:

    | Etapa | Comportamento esperado |
    |-------|----------------------|
    | Encerramento das receitas | O sistema debita as contas de receita para zerá-las e credita a conta de Apuração do Resultado do Exercício. |
    | Encerramento de custos e despesas | O sistema credita as contas de custos e despesas para zerá-las e debita a conta de Apuração do Resultado do Exercício. |
    | Confronto da apuração | O sistema compara receitas, deduções, custos e despesas para identificar o lucro. |
    | Transferência do resultado | Como houve lucro, o sistema debita Apuração do Resultado do Exercício e credita Lucros Acumulados. |

    Após clicar em **Realizar Apuração**, os lançamentos devem ser efetivados no Livro Diário. Também deve ser possível acessar o Histórico de Apurações, verificar a apuração realizada e, se necessário, desfazê-la.

    ### Validações após a apuração

    No Livro Diário, devem aparecer os lançamentos automáticos de encerramento das contas de resultado.

    No Livro Razão ou no Balancete de Verificação, deve ser possível validar que:

    - as contas de receita foram zeradas;
    - as contas de custos e despesas foram zeradas;
    - a conta de Apuração do Resultado do Exercício foi movimentada;
    - o lucro foi transferido para Lucros Acumulados;
    - o total de débitos e créditos continua equilibrado.

    ### Resultado esperado na DRE

    | Linha da DRE | Valor esperado |
    |-------------|---------------|
    | Receita Bruta | R$ 60.000,00 |
    | (-) Deduções da Receita | R$ 5.000,00 |
    | (=) Receita Líquida | R$ 55.000,00 |
    | (-) CMV / CPV | R$ 25.000,00 |
    | (=) Lucro Bruto | R$ 30.000,00 |
    | (-) Despesas Operacionais | R$ 9.500,00 |
    | (+/-) Resultado Financeiro | R$ 500,00 |
    | **(=) Resultado Líquido do Período** | **R$ 21.000,00** |

    A DRE deve refletir a apuração realizada e permitir expandir a composição das contas, mostrando quais contas entraram em cada grupo da demonstração.

    ### Resultado esperado no Balanço Patrimonial

    | Grupo | Valor esperado |
    |-------|---------------|
    | Ativo | R$ 159.000,00 |
    | Passivo | R$ 38.000,00 |
    | Patrimônio Líquido | R$ 121.000,00 |

    **Conferência:** Ativo = Passivo + Patrimônio Líquido → R$ 159.000,00 = R$ 38.000,00 + R$ 121.000,00

    O Patrimônio Líquido deve considerar:

    - Capital Social: R$ 100.000,00
    - Lucros Acumulados: R$ 21.000,00
    - **Total do Patrimônio Líquido: R$ 121.000,00**

=== "Resultado Neutro"

    ### Objetivo do teste

    Validar um cenário em que as receitas, deduções, custos e despesas se anulam, resultando em resultado igual a zero.

    ### Lançamentos no Livro Diário

    | Nº | Data | Conta Débito | Grupo da Conta Débito | Conta Crédito | Grupo da Conta Crédito | Valor | Histórico |
    |----|------|-------------|----------------------|--------------|----------------------|-------|-----------|
    | 1 | 01/02/2026 | Banco A | Ativo | Capital Social | Patrimônio Líquido | R$ 60.000,00 | Integralização de capital social no Banco A. |
    | 2 | 03/02/2026 | Mercadorias para Revenda | Ativo | Banco A | Ativo | R$ 25.000,00 | Compra de mercadorias para revenda paga pelo Banco A. |
    | 3 | 08/02/2026 | Banco A | Ativo | Venda de Mercadorias | Contas de Resultado — Receitas | R$ 30.000,00 | Venda de mercadorias recebida à vista no Banco A. |
    | 4 | 08/02/2026 | Custos das Mercadorias Vendidas | Contas de Resultado — Custos e Despesas | Mercadorias para Revenda | Ativo | R$ 18.000,00 | Baixa do estoque pelo custo das mercadorias vendidas. |
    | 5 | 08/02/2026 | Simples Nacional | Contas de Resultado — Receitas / Deduções | Simples Nacional a Recolher | Passivo | R$ 3.000,00 | Reconhecimento de imposto sobre a venda. |
    | 6 | 15/02/2026 | Salários e Ordenados e Encargos | Contas de Resultado — Custos e Despesas | Salários e Ordenados a Pagar | Passivo | R$ 7.000,00 | Apropriação de salários administrativos a pagar. |
    | 7 | 20/02/2026 | Energia Elétrica | Contas de Resultado — Custos e Despesas | Banco A | Ativo | R$ 2.000,00 | Pagamento de energia elétrica pelo Banco A. |
    | 8 | 25/02/2026 | Aplicações | Ativo | Banco A | Ativo | R$ 10.000,00 | Aplicação financeira realizada com recursos do Banco A. |

    ### Resultado esperado na apuração

    | Item | Valor esperado |
    |------|---------------|
    | Total de Receitas | R$ 30.000,00 |
    | Total de Custos e Despesas | R$ 30.000,00 |
    | Resultado do Período | R$ 0,00 |
    | Tipo de Resultado | **Neutro** |

    A apuração deve zerar as contas de resultado normalmente, mas o confronto final não deve gerar lucro nem prejuízo. Como o resultado é zero, não deve haver valor efetivo a transferir para Lucros Acumulados ou Prejuízos Acumulados.

    ### Validações após a apuração

    No Livro Diário, devem aparecer os lançamentos automáticos de encerramento das contas de resultado.

    No Livro Razão ou no Balancete de Verificação, deve ser possível confirmar que:

    - Venda de Mercadorias foi zerada;
    - Simples Nacional foi zerada;
    - Custos das Mercadorias Vendidas foi zerada;
    - Salários e Ordenados e Encargos foi zerada;
    - Energia Elétrica foi zerada;
    - o resultado final da apuração ficou em R$ 0,00.

    ### Resultado esperado na DRE

    | Linha da DRE | Valor esperado |
    |-------------|---------------|
    | Receita Bruta | R$ 30.000,00 |
    | (-) Deduções da Receita | R$ 3.000,00 |
    | (=) Receita Líquida | R$ 27.000,00 |
    | (-) CMV / CPV | R$ 18.000,00 |
    | (=) Lucro Bruto | R$ 9.000,00 |
    | (-) Despesas Operacionais | R$ 9.000,00 |
    | **(=) Resultado Líquido do Período** | **R$ 0,00** |

    A DRE deve refletir que a empresa não teve lucro nem prejuízo no período.

    ### Resultado esperado no Balanço Patrimonial

    | Grupo | Valor esperado |
    |-------|---------------|
    | Ativo | R$ 70.000,00 |
    | Passivo | R$ 10.000,00 |
    | Patrimônio Líquido | R$ 60.000,00 |

    **Conferência:** Ativo = Passivo + Patrimônio Líquido → R$ 70.000,00 = R$ 10.000,00 + R$ 60.000,00

=== "Prejuízo"

    ### Objetivo do teste

    Validar um cenário simples em que os custos e despesas são maiores que as receitas, resultando em prejuízo.

    ### Lançamentos no Livro Diário

    | Nº | Data | Conta Débito | Grupo da Conta Débito | Conta Crédito | Grupo da Conta Crédito | Valor | Histórico |
    |----|------|-------------|----------------------|--------------|----------------------|-------|-----------|
    | 1 | 01/03/2026 | Banco A | Ativo | Capital Social | Patrimônio Líquido | R$ 30.000,00 | Integralização de capital social no Banco A. |
    | 2 | 05/03/2026 | Banco A | Ativo | Serviços Prestados | Contas de Resultado — Receitas | R$ 5.000,00 | Recebimento à vista por serviços prestados. |
    | 3 | 10/03/2026 | Custos dos Serviços Prestados | Contas de Resultado — Custos e Despesas | Banco A | Ativo | R$ 8.000,00 | Pagamento de custos relacionados aos serviços prestados. |
    | 4 | 15/03/2026 | Energia Elétrica | Contas de Resultado — Custos e Despesas | Banco A | Ativo | R$ 3.000,00 | Pagamento de energia elétrica pelo Banco A. |

    ### Resultado esperado na apuração

    | Item | Valor esperado |
    |------|---------------|
    | Total de Receitas | R$ 5.000,00 |
    | Total de Custos e Despesas | R$ 11.000,00 |
    | Resultado do Período | R$ 6.000,00 |
    | Tipo de Resultado | **Prejuízo** |

    A apuração deve apresentar o encerramento das contas de resultado e identificar que os custos e despesas foram maiores que as receitas. Nesse caso, o sistema deve transferir o resultado para Prejuízos Acumulados.

    | Etapa | Comportamento esperado |
    |-------|----------------------|
    | Encerramento das receitas | O sistema debita Serviços Prestados e credita Apuração do Resultado do Exercício. |
    | Encerramento dos custos | O sistema debita Apuração do Resultado do Exercício e credita Custos dos Serviços Prestados. |
    | Encerramento das despesas | O sistema debita Apuração do Resultado do Exercício e credita Energia Elétrica. |
    | Transferência do prejuízo | O sistema debita Prejuízos Acumulados e credita Apuração do Resultado do Exercício. |

    ### Validações após a apuração

    No Livro Diário, devem constar os lançamentos automáticos gerados pela apuração.

    No Livro Razão ou no Balancete de Verificação, deve ser possível verificar que:

    - Serviços Prestados foi zerada;
    - Custos dos Serviços Prestados foi zerada;
    - Energia Elétrica foi zerada;
    - Apuração do Resultado do Exercício foi encerrada;
    - o prejuízo foi transferido para Prejuízos Acumulados.

    ### Resultado esperado na DRE

    | Linha da DRE | Valor esperado |
    |-------------|---------------|
    | Receita Bruta | R$ 5.000,00 |
    | (-) Deduções da Receita | R$ 0,00 |
    | (=) Receita Líquida | R$ 5.000,00 |
    | (-) CMV / CPV / Custos dos Serviços | R$ 8.000,00 |
    | (=) Lucro Bruto | -R$ 3.000,00 |
    | (-) Despesas Operacionais | R$ 3.000,00 |
    | **(=) Resultado Líquido do Período** | **-R$ 6.000,00** |

    A DRE deve refletir o prejuízo do período e permitir visualizar quais contas compõem cada etapa da demonstração.

    ### Resultado esperado no Balanço Patrimonial

    | Grupo | Valor esperado |
    |-------|---------------|
    | Ativo | R$ 24.000,00 |
    | Passivo | R$ 0,00 |
    | Patrimônio Líquido | R$ 24.000,00 |

    **Conferência:** Ativo = Passivo + Patrimônio Líquido → R$ 24.000,00 = R$ 0,00 + R$ 24.000,00

    O Patrimônio Líquido deve considerar:

    - Capital Social: R$ 30.000,00
    - Prejuízos Acumulados: -R$ 6.000,00
    - **Total do Patrimônio Líquido: R$ 24.000,00**

---

## Orientação geral para validação

Após cadastrar os lançamentos de qualquer cenário, siga este fluxo:

1. Acesse o **Livro Diário** e confira se todos os lançamentos foram registrados com débito e crédito equilibrados.
2. Acesse o **Livro Razão** para verificar a movimentação individual de cada conta.
3. Acesse o **Balancete de Verificação** para validar se o total de débitos e créditos está fechado.
4. Vá até a tela de **Apuração** e selecione o período correspondente.
5. Confira o resumo, as contas de resultado, os valores de encerramento, o confronto da apuração e a transferência final do lucro ou prejuízo.
6. Clique em **Realizar Apuração**.
7. Volte ao Livro Diário e valide os lançamentos automáticos gerados pelo sistema.
8. Confira no Livro Razão ou no Balancete se as contas de resultado foram zeradas.
9. Acesse a **DRE** e confirme se o resultado reflete a apuração realizada.
10. Acesse o **Balanço Patrimonial** e valide se Ativo = Passivo + Patrimônio Líquido. O balanço deve aparecer como fechado quando os lançamentos estiverem consistentes.
