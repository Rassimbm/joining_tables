Find all the clients (first and last name) billing amount and charged date
SELECT clients.first_name, clients.last_name, billing.amount, billing.charged_datetime
FROM clients
JOIN billing ON clients.id = billing.clients_id;

List all domain names and leads (first and last name) for each site
SELECT leads.first_name, leads.last_name, sites.domain_name
FROM sites
JOIN leads ON sites.id = leads.sites_id;
