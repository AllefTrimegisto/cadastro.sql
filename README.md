# cadastro.sql
#Crie uma função que some todos os clientes cadastrados em uma loja durante um dia.

CREATE FUNCTION total_customers_per_day(purchase_date DATE)
RETURNS INT
BEGIN
  DECLARE total INT;
  SELECT COUNT(DISTINCT customer_id) INTO total 
  FROM purchases 
  WHERE DATE(purchase_date) = purchase_date;
  RETURN total;
END;

#Neste exemplo, a função total_customers_per_day recebe uma data de compra como entrada e retorna o número total de clientes únicos que fizeram compras #nessa data. A função usa uma consulta para contar o número de IDs de clientes distintos nas tabelas de compras onde a data da compra corresponde à data de #entrada.

#Aqui está um exemplo de como a função poderia ser escrita em SQL para o PostgreSQL:

CREATE FUNCTION total_customers_per_day(purchase_date DATE)
RETURNS INTEGER AS $$
DECLARE
  total INTEGER;
BEGIN
  SELECT COUNT(DISTINCT customer_id) INTO total 
  FROM purchases 
  WHERE DATE(purchase_date) = purchase_date;
  RETURN total;
END;
$$ LANGUAGE plpgsql;

