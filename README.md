Projeto Para Menção Do 3° Bimestre do Martelo

# Projeto Laravel - Fornecedores

Projeto em PHP com uso do Laravel para gerenciar tabelas e registros do banco de dados, e executar migrations de criação e alteração.

## 📌 Requisitos para execução:

- PHP (>= 8.0)
- Composer (gerenciador de dependências PHP)
- MySQL (instalado e rodando)
- VS Code ou outro editor de código

## 🚀 Tutorial

### 1️⃣ Instalação do Laravel
No terminal, execute o comando:

```bash
laravel new fornecedores
````
### 3️⃣ Criando as migrations

Dentro da pasta do projeto, execute:

```bash
php artisan make:migration create_fornecedores_table
php artisan make:migration create_cadastro_table
php artisan make:migration alter_fornecedores_table
```

#### 📷 Print da criação das migrations: Execução da migration

Nos arquivos gerados em `database/migrations/`, adicione os campos desejados:

```php
public function up(): void
    {
        Schema::create('cadastro', function (Blueprint $table) {
                $table->id();
                $table->string('nome');
                $table->string('endereco');
                $table->string('telefone');
                $table->string('cnpj')->unique();
                $table->timestamps();
            });
    }
```

```php
// create_estoque_table
public function up(): void
    {
        Schema::create('estoque', function (Blueprint $table) {
                $table->id();
                $table->integer('quantidade');
                $table->double('valor_unitario');
                $table->foreignId('cadastro_id')->constrained('cadastro')->onDelete('cascade');
                $table->timestamps();
            });
    }
```

```php
// alter_fornecedores_table
public function up(): void
    {
        Schema::table('cadastro', function (Blueprint $table) {
                $table->string('razao_social')->unique();
                $table->string('nome_fantasia')->unique();
            });
    }
```

### 4️⃣ Rodando as migrations

Execute no terminal:

```bash
php artisan migrate:fresh
```

#### 📷 Print da execução das migrations

### 🗄 Arquivo SQL do banco de dados

O arquivo `cavalcante.sql` contém o script para criação da tabela diretamente no MySQL.

### 🔗 Versionamento

O código completo está disponível no GitHub:

* **Repositório**: [https://github.com/EduardoSousaCavalcante/Atividade13-08](https://github.com/EduardoSousaCavalcante/Atividade13-08)
