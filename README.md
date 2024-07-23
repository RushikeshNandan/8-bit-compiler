git clone https://github.com/RushikeshNandan/8bit-computer.git
cd 8bit-computer
less README.md
cd rtl
#include <iostream>
#include <vector>
#include <string>
#include <cctype>

enum TokenType {
    KEYWORD, IDENTIFIER, OPERATOR, LITERAL, UNKNOWN
};

struct Token {
    TokenType type;
    std::string value;
};

std::vector<Token> tokenize(const std::string& code) {
    std::vector<Token> tokens;
    std::string current;
    for (char ch : code) {
        if (std::isspace(ch)) {
            if (!current.empty()) {
                tokens.push_back({UNKNOWN, current});
                current.clear();
            }
        } else if (std::isalpha(ch)) {
            current += ch;
        } else if (std::isdigit(ch)) {
            current += ch;
        } else {
            if (!current.empty()) {
                tokens.push_back({UNKNOWN, current});
                current.clear();
            }
            tokens.push_back({OPERATOR, std::string(1, ch)});
        }
    }
    if (!current.empty()) {
        tokens.push_back({UNKNOWN, current});
    }
    return tokens;
}

int main() {
    std::string code = "int a = b + 5;";
    std::vector<Token> tokens = tokenize(code);

    for (const Token& token : tokens) {
        std::cout << "Token: " << token.value << std::endl;
    }

    #include <iostream>
#include <vector>
#include <string>

enum NodeType {
    VAR_DECL, ASSIGNMENT, ARITHMETIC, CONDITIONAL, LOOP
};

struct ASTNode {
    NodeType type;
    std::vector<ASTNode> children;
    std::string value;
};

ASTNode parse(const std::vector<Token>& tokens) {
    // Implement your parsing logic here
    ASTNode root;
    return root;
}

int main() {
    std::string code = "int a = b + 5;";
    std::vector<Token> tokens = tokenize(code);
    ASTNode ast = parse(tokens);

    // Implement a function to print the AST
    printAST(ast);

    return 0;
}


#include <iostream>
#include <vector>
#include <string>

void generateAssembly(ASTNode node) {
    // Implement your code generation logic here
    switch (node.type) {
        case VAR_DECL:
            // Generate assembly for variable declaration
            break;
        case ASSIGNMENT:
            // Generate assembly for assignment
            break;
        case ARITHMETIC:
            // Generate assembly for arithmetic operations
            break;
        case CONDITIONAL:
            // Generate assembly for conditionals
            break;
        case LOOP:
            // Generate assembly for loops
            break;
    }
}

int main() {
    std::string code = "int a = b + 5;";
    std::vector<Token> tokens = tokenize(code);
    ASTNode ast = parse(tokens);

    generateAssembly(ast);

    return 0;
}



    return 0;
}
 
