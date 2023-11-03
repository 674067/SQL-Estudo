# SQL-Estudo
select meziat.dbo.TbProdutos.iCodProduto, sDscProduto, nValCusto, nValVenda, nQuantidade,  
round ((nQuantidade * nValVenda), 2) as Total_faturado,
round (-(nValCusto - nValVenda) / nValVenda, 2) as Margem, 
case
  when nValVenda >= 20 then 'Ótimo'  
  when nValVenda >= 15 then 'Bom'
  else 'low'
  end AS Avaliação_preço
from meziat.dbo.TbPrecoProduto
left join meziat.dbo.TbProdutos
on meziat.dbo.TbprecoProduto.iCodProduto = meziat.dbo.TbProdutos.iCodProduto 
left join meziat.dbo.TbProduto_NFCe
on meziat.dbo.TbProdutos.iCodProduto = meziat.dbo.TbProduto_NFCe.iCodProduto
where sDscProduto like 'pão_%'          
