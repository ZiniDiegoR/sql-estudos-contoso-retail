# sql-estudos-contoso-retail
Praticando SQL na prática: consultas de negócio com MAX, AVG, COUNT, ROUND e GROUP BY na base ContosoRetailDW


-- quantos produtos temos na empresa 
select *
from DimProduct

-- produto mais caro da empresa

select max(UnitPrice) from DimProduct

--qual a média dos preços dos produtos 

select 
round(AVG(unitprice),2)
from DimProduct

-- quantas marcas temos na empresa 

select 
count(distinct(BrandName))
from DimProduct

-- exiba as marcas da empresa usando a função 'group by'

select 
BrandName,
max(unitprice) as 'preço maximo'
from DimProduct
group by BrandName

-- exiba todas as marcas e todas as classes 

select
brandname,
classname,
round(AVG(UnitPrice), 2) as 'preço medio'
from DimProduct
where ClassName= 'economy' and BrandName= 'contoso'
group by BrandName, ClassName

--qual media de preço da classe economica 

select
classname,
round(AVG(unitprice),2) as 'preço medio'
from DimProduct
where ClassName= 'economy'
group by ClassName

--exbida a tabela de produtos
--(nome produto, marca, preço)
--ordene do mais caro para o mais barato
--exiba os 10 produtos mais baratos


select top 20
ProductName,
brandname,
UnitPrice
from DimProduct
order by UnitPrice asc
