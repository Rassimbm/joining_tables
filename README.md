1-JOIN:
Find all the clients (first and last name) billing amount and charged date
SELECT clients.first_name, clients.last_name, billing.amount, billing.charged_datetime
FROM clients
JOIN billing ON clients.id = billing.clients_id;

List all domain names and leads (first and last name) for each site
SELECT leads.first_name, leads.last_name, sites.domain_name
FROM sites
JOIN leads ON sites.id = leads.sites_id;

2-JOIN ON MULTIPLE TABLES:
Get the names of the clients, their domain names and the first name of all leads generated from those sites
SELECT clients.first_name AS clients_f_name, clients.last_name, sites.domain_name, leads.first_name AS leads_f_name
FROM  clients
JOIN sites ON clients.id = sites.clients_id
JOIN leads ON sites.id = leads.sites_id;

3-LEFT & RIGHT JOIN:
List all the clients and the sites each client has, even if the client hasn't landed a site yet
SELECT clients.first_name, clients.last_name, sites.domain_name
FROM clients
LEFT JOIN sites ON clients.id = sites.clients_id;

4-GROUPING ROWS: GROUP BY (SUM, MIN, MAX, AVG):
Find all the clients(first and last name) and their total billing amounts
SELECT clients.first_name, clients.last_name, SUM(billing.amount)
FROM clients
JOIN billing ON clients.id = billing.clients_id
GROUP BY clients.id;

5-GROUP_CONCAT:
List all the domain names associated with each client
SELECT clients.first_name, clients.last_name, GROUP_CONCAT(sites.domain_name) AS domain_names
FROM clients
JOIN sites ON clients.id = sites.clients_id
GROUP BY clients.id;
