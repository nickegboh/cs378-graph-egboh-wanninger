
```

// ----------------------------
// projects/graph/TestGraph.c++
// Copyright (C) 2010
// Glenn P. Downing
// ----------------------------

/*
To test the program:
    % g++ -ansi -pedantic -I/public/linux/include/boost-1_38 -lcppunit -ldl -Wall TestGraph.c++ -o TestGraph.app
    % valgrind TestGraph.app >& TestGraph.c++.out
*/

// --------
// includes
// --------

#include <iostream> // cout, endl
#include <iterator> // ostream_iterator
#include <sstream>  // ostringstream
#include <utility>  // pair

#include "boost/graph/adjacency_list.hpp" // adjacency_list

#include "cppunit/extensions/HelperMacros.h" // CPPUNIT_TEST, CPPUNIT_TEST_SUITE, CPPUNIT_TEST_SUITE_END
#include "cppunit/TestFixture.h"             // TestFixture
#include "cppunit/TestSuite.h"               // TestSuite
#include "cppunit/TextTestRunner.h"          // TestRunner

#include "Graph.h"
#include "GraphAlgorithms.h"

// ---------
// TestGraph
// ---------

template <typename T>
struct TestGraph : CppUnit::TestFixture {
    // --------
    // typedefs
    // --------

    typedef T                                       graph_type;

    typedef typename graph_type::vertex_descriptor  vertex_descriptor;
    typedef typename graph_type::edge_descriptor    edge_descriptor;

    typedef typename graph_type::vertex_iterator    vertex_iterator;
    typedef typename graph_type::edge_iterator      edge_iterator;
    typedef typename graph_type::adjacency_iterator adjacency_iterator;

    typedef typename graph_type::vertices_size_type vertices_size_type;
    typedef typename graph_type::edges_size_type    edges_size_type;

    // -----
    // tests
    // -----

    graph_type g;
    graph_type g2;
    graph_type g3;
    graph_type g4;
    graph_type g5;
    graph_type g6;
    graph_type g7;
    graph_type g8;
    graph_type g9;
    graph_type g10;
   	graph_type g11;
    graph_type g12;
    graph_type g13;

    vertex_descriptor vdA;
    vertex_descriptor vdB;
    vertex_descriptor vdC;
    vertex_descriptor vdD;
    vertex_descriptor vdE;
    vertex_descriptor vdF;
    vertex_descriptor vdG;
    vertex_descriptor vdH;
    
	edge_descriptor edAA;
    edge_descriptor edAB;
    edge_descriptor edAC;
    edge_descriptor edAE;
    edge_descriptor edAG;
    edge_descriptor edAH;
    edge_descriptor edBD;
    edge_descriptor edBE;
    edge_descriptor edCD;
    edge_descriptor edDE;
    edge_descriptor edDF;
    edge_descriptor edFD;
    edge_descriptor edFH;
    edge_descriptor edGH;
    edge_descriptor edGA;
    
    vertex_descriptor vd13A;
        vertex_descriptor vd13B;
        vertex_descriptor vd13C;
        vertex_descriptor vd13D;
        vertex_descriptor vd13E;
        vertex_descriptor vd13F;
        vertex_descriptor vd13G;
        vertex_descriptor vd13H;
        vertex_descriptor vd13I;

        edge_descriptor ed13AE;
        edge_descriptor ed13AB;
        edge_descriptor ed13BE;
        edge_descriptor ed13EH;
        edge_descriptor ed13HC;
        edge_descriptor ed13CI;
        edge_descriptor ed13BF;
        edge_descriptor ed13FG;
        edge_descriptor ed13FI;
        edge_descriptor ed13GI;
        edge_descriptor ed13DI;

        graph_type _h;
        vertex_descriptor _hA;
        vertex_descriptor _hB;
        vertex_descriptor _hC;
        edge_descriptor _eAB;
        edge_descriptor _eBC;
        edge_descriptor _eCA;    
                        

        graph_type _g;

        vertex_descriptor _vdA;
        vertex_descriptor _vdB;
        vertex_descriptor _vdC;
        vertex_descriptor _vdD;
        vertex_descriptor _vdE;
        vertex_descriptor _vdF;
        vertex_descriptor _vdG;
        vertex_descriptor _vdH;

		edge_descriptor _edAB;
        edge_descriptor _edAC;
        edge_descriptor _edAE;
        edge_descriptor _edBD;
        edge_descriptor _edBE;
        edge_descriptor _edCD;
        edge_descriptor _edDE;
        edge_descriptor _edDF;
        edge_descriptor _edFH;
        edge_descriptor _edGH;

    // -----
    // setUp
    // -----

    // directed, sparse, unweighted
    // possibly connected
    // possibly cyclic
    // Collins, 2nd, pg. 653
    void setUp () {
        vdA  = add_vertex(g);
        vdB  = add_vertex(g);
        vdC  = add_vertex(g);
        vdD  = add_vertex(g);
        vdE  = add_vertex(g);
        vdF  = add_vertex(g);
        vdG  = add_vertex(g);
        vdH  = add_vertex(g);
        edAB = add_edge(vdA, vdB, g).first;
        edAC = add_edge(vdA, vdC, g).first;
        edAE = add_edge(vdA, vdE, g).first;
        edBD = add_edge(vdB, vdD, g).first;
        edBE = add_edge(vdB, vdE, g).first;
        edCD = add_edge(vdC, vdD, g).first;
        edDE = add_edge(vdD, vdE, g).first;
        edDF = add_edge(vdD, vdF, g).first;
        edFD = add_edge(vdF, vdD, g).first;
        edFH = add_edge(vdF, vdH, g).first;
        edGH = add_edge(vdG, vdH, g).first;
        vertex_descriptor vd3A = add_vertex(g3);
                vertex_descriptor vd3B = add_vertex(g3);
                vertex_descriptor vd3C = add_vertex(g3);
                vertex_descriptor vd3D = add_vertex(g3);
                                                                 add_vertex(g3);
                vertex_descriptor vd3F = add_vertex(g3);
                add_edge(vd3A, vd3B, g3).first;
                add_edge(vd3B, vd3C, g3).first;
                add_edge(vd3C, vd3D, g3).first;
                add_edge(vd3D, vd3F, g3).first;
                add_edge(vd3F, vd3A, g3).first;

                add_vertex(g4);
                add_vertex(g4);
                add_vertex(g4);
                add_vertex(g4);
                add_vertex(g4);
                
                vertex_descriptor vd5A = add_vertex(g5);
                vertex_descriptor vd5B = add_vertex(g5);
                vertex_descriptor vd5C = add_vertex(g5);
                vertex_descriptor vd5D = add_vertex(g5);
                vertex_descriptor vd5E = add_vertex(g5);
                add_edge(vd5A, vd5B, g5);
                add_edge(vd5A, vd5C, g5);
                add_edge(vd5A, vd5D, g5);
                add_edge(vd5D, vd5E, g5);
                
                vertex_descriptor vd6A = add_vertex(g6);
                vertex_descriptor vd6B = add_vertex(g6);
                vertex_descriptor vd6C = add_vertex(g6);
                vertex_descriptor vd6D = add_vertex(g6);
                vertex_descriptor vd6E = add_vertex(g6);
                vertex_descriptor vd6F = add_vertex(g6);
                add_edge(vd6A, vd6B, g6); 
                add_edge(vd6B, vd6C, g6); 
                add_edge(vd6C, vd6D, g6); 
                add_edge(vd6D, vd6F, g6); 
                add_edge(vd6F, vd6E, g6); 
                
                vertex_descriptor vd7A = add_vertex(g7);
                vertex_descriptor vd7B = add_vertex(g7);
                vertex_descriptor vd7C = add_vertex(g7);
                add_edge(vd7C, vd7A, g7);
                add_edge(vd7C, vd7B, g7);
                
                vertex_descriptor vd8A = add_vertex(g8);
                vertex_descriptor vd8B = add_vertex(g8);
                //vertex_descriptor vd7C = add_vertex(g7);
                add_edge(vd8A, vd8B, g8);
                add_edge(vd8B, vd8A, g8);
                
                vertex_descriptor vd9A = add_vertex(g9);
                vertex_descriptor vd9B = add_vertex(g9);
                vertex_descriptor vd9C = add_vertex(g9);
                vertex_descriptor vd9D = add_vertex(g9);
                vertex_descriptor vd9E = add_vertex(g9);
                add_edge(vd9A, vd9D, g9);
                add_edge(vd9B, vd9D, g9);
            add_edge(vd9C, vd9D, g9);
                add_edge(vd9D, vd9E, g9);
                
                vertex_descriptor vd10A = add_vertex(g10);
                vertex_descriptor vd10B = add_vertex(g10);
                vertex_descriptor vd10C = add_vertex(g10);
                vertex_descriptor vd10D = add_vertex(g10);
                vertex_descriptor vd10E = add_vertex(g10);
                vertex_descriptor vd10F = add_vertex(g10);
                vertex_descriptor vd10G = add_vertex(g10);
                add_edge(vd10A, vd10D, g10);
                add_edge(vd10B, vd10D, g10);
            add_edge(vd10C, vd10D, g10);
                add_edge(vd10D, vd10E, g10);
                add_edge(vd10F, vd10G, g10);
                add_edge(vd10G, vd10F, g10);            
                
                vertex_descriptor vd11A = add_vertex(g11); 
        vertex_descriptor vd11B = add_vertex(g11); 
        vertex_descriptor vd11C = add_vertex(g11); 
        vertex_descriptor vd11D = add_vertex(g11); 
        vertex_descriptor vd11E = add_vertex(g11); 
        vertex_descriptor vd11F = add_vertex(g11); 
        vertex_descriptor vd11G = add_vertex(g11); 
        vertex_descriptor vd11H = add_vertex(g11); 
        add_edge(vd11A, vd11B, g11).first; 
        add_edge(vd11A, vd11C, g11).first; 
        add_edge(vd11A, vd11E, g11).first; 
        add_edge(vd11B, vd11D, g11).first; 
        add_edge(vd11B, vd11E, g11).first; 
        add_edge(vd11C, vd11D, g11).first; 
        add_edge(vd11D, vd11E, g11).first; 
        add_edge(vd11D, vd11F, g11).first; 
        add_edge(vd11F, vd11D, g11).first; 
        add_edge(vd11F, vd11H, g11).first; 
        add_edge(vd11G, vd11H, g11).first; 
                
                vertex_descriptor vd12A = add_vertex(g12);
                vertex_descriptor vd12B = add_vertex(g12);
                vertex_descriptor vd12C = add_vertex(g12);
                vertex_descriptor vd12D = add_vertex(g12);
                add_edge(vd12A, vd12B, g12);
                add_edge(vd12A, vd12C, g12);
            add_edge(vd12C, vd12D, g12);
                add_edge(vd12B, vd12D, g12);
                
        vd13A = add_vertex( g13 ); 
        vd13B = add_vertex( g13 ); 
        vd13C = add_vertex( g13 ); 
        vd13D = add_vertex( g13 ); 
        vd13E = add_vertex( g13 ); 
        vd13F = add_vertex( g13 ); 
        vd13G = add_vertex( g13 ); 
        vd13H = add_vertex( g13 ); 
        vd13I = add_vertex( g13 ); 
 
        ed13AE = add_edge( vd13A, vd13E, g13 ).first; 
        ed13AB = add_edge(vd13A, vd13B, g13 ).first; 
        ed13BE = add_edge( vd13B, vd13E, g13 ).first; 
        ed13EH = add_edge( vd13E, vd13H, g13 ).first; 
        ed13HC = add_edge( vd13H, vd13C, g13 ).first; 
        ed13CI = add_edge( vd13C, vd13I, g13 ).first; 
        ed13BF = add_edge( vd13B, vd13F, g13 ).first; 
        ed13FG = add_edge( vd13F, vd13G, g13 ).first; 
        ed13FI = add_edge( vd13F, vd13I, g13 ).first; 
        ed13GI = add_edge( vd13G, vd13I, g13 ).first; 
        ed13DI = add_edge( vd13D, vd13I, g13 ).first;

        _hA = add_vertex(_h);
        
        _hB = add_vertex(_h);        
        _hC = add_vertex(_h);
        
        _eAB = add_edge(_hA, _hB, _h).first;
        _eBC = add_edge(_hB, _hC, _h).first;
        _eCA = add_edge(_hC, _hA, _h).first;

        _vdA  = add_vertex(_g);
        _vdB  = add_vertex(_g);
        _vdC  = add_vertex(_g);
        _vdD  = add_vertex(_g);
        _vdE  = add_vertex(_g);
        _vdF  = add_vertex(_g);
        _vdG  = add_vertex(_g);
        _vdH  = add_vertex(_g);
        int i = 0;
        assert(_vdA == vertex(i++, _g));
        assert(_vdB == vertex(i++, _g));
        assert(_vdC == vertex(i++, _g));
        assert(_vdD == vertex(i++, _g));
        assert(_vdE == vertex(i++, _g));
        assert(_vdF == vertex(i++, _g));
        assert(_vdG == vertex(i++, _g));
        assert(_vdH == vertex(i++, _g));
                                                                
        _edAB = add_edge(_vdA, _vdB, _g).first;
        _edAC = add_edge(_vdA, _vdC, _g).first;
        _edAE = add_edge(_vdA, _vdE, _g).first;
        _edBD = add_edge(_vdB, _vdD, _g).first;
        _edBE = add_edge(_vdB, _vdE, _g).first;
        _edCD = add_edge(_vdC, _vdD, _g).first;
        _edDE = add_edge(_vdD, _vdE, _g).first;
        _edDF = add_edge(_vdD, _vdF, _g).first;
        _edFH = add_edge(_vdF, _vdH, _g).first;
        _edGH = add_edge(_vdG, _vdH, _g).first;}
        

    // -------------
    // test_add_edge
    // -------------

    void test_add_edge () {
    	//std::cout << edAB << std::endl;
    	//std::cout << vdA << vdB << vdC << std::endl;
    	//std::cout << num_vertices(g) << std::endl;
        std::pair<edge_descriptor, bool> p = add_edge(vdA, vdB, g);
        //std::cout << (&edAB == &p.first) << std::endl;
        CPPUNIT_ASSERT(p.first  == edAB);
        CPPUNIT_ASSERT(p.second == false);}
        
    void test_add_edge_2 () {
        std::pair<edge_descriptor, bool> p = add_edge(vdA, vdC, g);
        CPPUNIT_ASSERT(p.first  == edAC);
        CPPUNIT_ASSERT(p.second == false);}
        
     void test_add_edge_3 () {
        std::pair<edge_descriptor, bool> p = add_edge(vdB, vdA, g);
        CPPUNIT_ASSERT(p.second == true);}

    // ----------------------
    // test_adjacent_vertices
    // ----------------------

    void test_adjacent_vertices () {
        std::pair<adjacency_iterator, adjacency_iterator> p = adjacent_vertices(vdA, g);
        adjacency_iterator b = p.first;
        adjacency_iterator e = p.second;
        CPPUNIT_ASSERT(b != e);
        if (b != e) {
            vertex_descriptor vd = *b;
            CPPUNIT_ASSERT(vd == vdB);}
        ++b;
        if (b != e) {
            vertex_descriptor vd = *b;
            CPPUNIT_ASSERT(vd == vdC);}
        ++b;
        if (b != e) {
            vertex_descriptor vd = *b;
            CPPUNIT_ASSERT(vd == vdE);
        }
        b++;
        CPPUNIT_ASSERT( b == e );
        
        p = adjacent_vertices(vdH, g);
        b = p.first;
        e = p.second;
        CPPUNIT_ASSERT(b == e);
  	}

    // ---------
    // test_edge
    // ---------

    void test_edge () {
        std::pair<edge_descriptor, bool> p = edge(vdA, vdB, g);
        CPPUNIT_ASSERT(p.first  == edAB);
        CPPUNIT_ASSERT(p.second == true);}
        
    void test_edge_2 () {
        std::pair<edge_descriptor, bool> p = edge(vdD, vdE, g);
        CPPUNIT_ASSERT(p.first  == edDE);
        CPPUNIT_ASSERT(p.second == true);}
        
    void test_edge_3 () {
        std::pair<edge_descriptor, bool> p = edge(vdG, vdF, g);
        CPPUNIT_ASSERT(p.second == false);}

    // ----------
    // test_edges
    // ----------

    void test_edges () {
        std::pair<edge_iterator, edge_iterator> p = edges(g);
        edge_iterator                           b = p.first;
        edge_iterator                           e = p.second;
        CPPUNIT_ASSERT(b != e);
        if (b != e) {
            edge_descriptor ed = *b;
            CPPUNIT_ASSERT(ed == edAB);
        }
        ++b;
        if (b != e) {
            edge_descriptor ed = *b;
            CPPUNIT_ASSERT(ed == edAC);
        }
        ++b;
        if (b != e) {
            edge_descriptor ed = *b;
            CPPUNIT_ASSERT(ed == edAE);
        }
        ++b;
        if (b != e) {
            edge_descriptor ed = *b;
            CPPUNIT_ASSERT(ed == edBD);
        }
        
        graph_type gr =  graph_type();
        p = edges( gr );
        CPPUNIT_ASSERT(p.first == p.second);    }

    // --------------
    // test_num_edges
    // --------------

    void test_num_edges () {
        edges_size_type es = num_edges(g);
        CPPUNIT_ASSERT(es == 11);
     }
        
    void test_num_edges_2 () {
    	graph_type gr =  graph_type();
        edges_size_type es = num_edges(gr);
        CPPUNIT_ASSERT(es == 0);
    }
    
    void test_num_edges_3 () {
    	graph_type gr =  graph_type();
    	vertex_descriptor vdA = add_vertex( gr );
        vertex_descriptor vdB = add_vertex( gr );
        std::pair<edge_descriptor, bool> p = add_edge(vdA, vdB, gr);
        edges_size_type es = num_edges(gr);
        CPPUNIT_ASSERT(es == 1);	
    }

    // -----------------
    // test_num_vertices
    // -----------------

    void test_num_vertices () {
        vertices_size_type vs = num_vertices(g);
        CPPUNIT_ASSERT(vs == 8);
        
        graph_type gr =  graph_type();
        vertices_size_type es = num_vertices(gr);
        CPPUNIT_ASSERT(es == 0);
        
        add_vertex( gr );
        es = num_vertices(gr);
        CPPUNIT_ASSERT(es == 1);

        add_vertex( gr );
        es = num_vertices(gr);
        CPPUNIT_ASSERT(es == 2);}

    // -----------
    // test_source
    // -----------

    void test_source () {
        vertex_descriptor vd = source(edAB, g);
        CPPUNIT_ASSERT(vd == vdA);}
        
	void test_source_2 () {
		vertex_descriptor vd = source(edFD, g);
        CPPUNIT_ASSERT(vd == vdF);
    }
    
    void test_source_3 () {
		vertex_descriptor vd = source(std::make_pair(vdA,vdF), g);
        CPPUNIT_ASSERT(vd == vdA);
    }

    // -----------
    // test_target
    // -----------

    void test_target () {
        vertex_descriptor vd = target(edAB, g);
        CPPUNIT_ASSERT(vd == vdB);}

    // -----------
    // test_vertex
    // -----------

    void test_vertex () {
        vertex_descriptor vd = vertex(0, g);
        CPPUNIT_ASSERT(vd == vdA);}

    // -------------
    // test_vertices
    // -------------

    void test_vertices () {
        std::pair<vertex_iterator, vertex_iterator> p = vertices(g);
        vertex_iterator                             b = p.first;
        vertex_iterator                             e = p.second;
        CPPUNIT_ASSERT(b != e);
        if (b != e) {
            vertex_descriptor vd = *b;
            CPPUNIT_ASSERT(vd == vdA);}
        ++b;
        if (b != e) {
            vertex_descriptor vd = *b;
            CPPUNIT_ASSERT(vd == vdB);}}
            
    void test_vertices_2 () {
        std::pair<vertex_iterator, vertex_iterator> p = vertices(g);
        vertex_iterator                             b = p.first;
        vertex_iterator                             e = p.second;

        for( vertices_size_type nv = 0; nv < num_vertices(g); nv++ ) {
                CPPUNIT_ASSERT(b != e);
                CPPUNIT_ASSERT(*b == vertex(nv, g) );
                b++;
        }
    }

    // --------------
    // test_has_cycle
    // --------------

    void test_has_cycle () {
        CPPUNIT_ASSERT(has_cycle(g));}
        
    void test_has_cycle_2 () {
    	graph_type gr =  graph_type();
        vertex_descriptor gr_vdA = add_vertex( gr );
        vertex_descriptor gr_vdB = add_vertex( gr );
        vertex_descriptor gr_vdC = add_vertex( gr );

        CPPUNIT_ASSERT( !has_cycle(gr) );
        edge_descriptor gr_vdAB = add_edge( gr_vdA, gr_vdB, gr ).first;
        edge_descriptor gr_vdBC = add_edge( gr_vdB, gr_vdC, gr ).first;
        CPPUNIT_ASSERT( !has_cycle(gr) );
        edge_descriptor gr_vdCA = add_edge( gr_vdC, gr_vdA, gr ).first;
        CPPUNIT_ASSERT( has_cycle(gr) );
     }
    

    void test_has_cycle_3 () {
        CPPUNIT_ASSERT(has_cycle(g3));}

    void test_has_cycle_4 () {
        CPPUNIT_ASSERT(!has_cycle(g4));}

    void test_has_cycle_5 () {
        CPPUNIT_ASSERT(!has_cycle(g5));}
                
    void test_has_cycle_6 () {
        CPPUNIT_ASSERT(!has_cycle(g6));}
                
    void test_has_cycle_7 () {
        CPPUNIT_ASSERT(!has_cycle(g7));}

    void test_has_cycle_8 () {
        CPPUNIT_ASSERT(has_cycle(g8));}
                
    void test_has_cycle_9 () {
        CPPUNIT_ASSERT(!has_cycle(g9));}
                
    void test_has_cycle_10 () {
        CPPUNIT_ASSERT(has_cycle(g10));}

    void test_has_cycle_11 () {
        CPPUNIT_ASSERT(has_cycle(g11));}
                
    void test_has_cycle_12 () {
        CPPUNIT_ASSERT(!has_cycle(g12));}
                
    void test_has_cycle_13 () {
        CPPUNIT_ASSERT(!has_cycle(g13));}
        
    void test_has_cycle_14 () {
        CPPUNIT_ASSERT(!has_cycle(g2));}

    // ---------------------
    // test_topological_sort
    // ---------------------

    void test_topological_sort () {
        std::ostringstream out;
        topological_sort(g4, std::ostream_iterator<vertex_descriptor>(out, " "));
        //std::cout << out.str() << std::endl;
        CPPUNIT_ASSERT(out.str() == "0 1 2 3 4 ");}

    void test_topological_sort_2 () {
        std::ostringstream out;
        topological_sort(g2, std::ostream_iterator<vertex_descriptor>(out, " "));
        CPPUNIT_ASSERT(out.str() == "");}
                
    void test_topological_sort_3 () {
        std::ostringstream out;
        topological_sort(g5, std::ostream_iterator<vertex_descriptor>(out, " "));
        CPPUNIT_ASSERT(out.str() == "1 2 4 3 0 ");}
                
    void test_topological_sort_4 () {
        std::ostringstream out;
        topological_sort(g6, std::ostream_iterator<vertex_descriptor>(out, " "));
        CPPUNIT_ASSERT(out.str() == "4 5 3 2 1 0 ");}
                
    void test_topological_sort_5 () {
        std::ostringstream out;
        topological_sort(g7, std::ostream_iterator<vertex_descriptor>(out, " "));
        CPPUNIT_ASSERT(out.str() == "0 1 2 ");}
                
    void test_topological_sort_6 () {
        std::ostringstream out;
        topological_sort(g9, std::ostream_iterator<vertex_descriptor>(out, " "));
        CPPUNIT_ASSERT(out.str() == "4 3 0 1 2 ");}

    void test_topological_sort_7 () {
        std::ostringstream out;
        topological_sort(g13, std::ostream_iterator<vertex_descriptor>(out, " "));
        CPPUNIT_ASSERT(out.str() == "8 2 7 4 6 5 1 0 3 ");}


    // -----
    // suite
    // -----

    CPPUNIT_TEST_SUITE(TestGraph);
    CPPUNIT_TEST(test_add_edge);
    CPPUNIT_TEST(test_add_edge_2);
    CPPUNIT_TEST(test_add_edge_3);
    CPPUNIT_TEST(test_adjacent_vertices);
    CPPUNIT_TEST(test_edge);
    CPPUNIT_TEST(test_edge_2);
    CPPUNIT_TEST(test_edge_3);
    CPPUNIT_TEST(test_edges);
    CPPUNIT_TEST(test_num_edges);
    CPPUNIT_TEST(test_num_edges_2);
    CPPUNIT_TEST(test_num_edges_3);
    CPPUNIT_TEST(test_num_vertices);
    CPPUNIT_TEST(test_source);
    CPPUNIT_TEST(test_source_2);
    CPPUNIT_TEST(test_source_3);
    CPPUNIT_TEST(test_target);
    CPPUNIT_TEST(test_vertex);
    CPPUNIT_TEST(test_vertices);
    CPPUNIT_TEST(test_vertices_2);
    CPPUNIT_TEST(test_has_cycle);
    CPPUNIT_TEST(test_has_cycle_2);
    CPPUNIT_TEST(test_has_cycle_3);
    CPPUNIT_TEST(test_has_cycle_4);
    CPPUNIT_TEST(test_has_cycle_5);
    CPPUNIT_TEST(test_has_cycle_6);
    CPPUNIT_TEST(test_has_cycle_7);
    CPPUNIT_TEST(test_has_cycle_8);
    CPPUNIT_TEST(test_has_cycle_9);
    CPPUNIT_TEST(test_has_cycle_10);
    CPPUNIT_TEST(test_has_cycle_11);
    CPPUNIT_TEST(test_has_cycle_12);
    CPPUNIT_TEST(test_has_cycle_13);
    CPPUNIT_TEST(test_has_cycle_14);
    CPPUNIT_TEST(test_topological_sort);
    CPPUNIT_TEST(test_topological_sort_2);
    CPPUNIT_TEST(test_topological_sort_3);
    CPPUNIT_TEST(test_topological_sort_4);
    CPPUNIT_TEST(test_topological_sort_5);
    CPPUNIT_TEST(test_topological_sort_6);
    CPPUNIT_TEST(test_topological_sort_7);
    CPPUNIT_TEST_SUITE_END();};


// ----
// main
// ----

int main () {
    using namespace std;
    using namespace boost;

    ios_base::sync_with_stdio(false); // turn off synchronization with C I/O
    cout << "TestGraph.c++" << endl;

    CppUnit::TextTestRunner tr;
    tr.addTest(TestGraph< adjacency_list<setS, vecS, directedS> >::suite());
    tr.addTest(TestGraph<Graph>::suite());
    tr.run();

    cout << "Done." << endl;
    return 0;}

```