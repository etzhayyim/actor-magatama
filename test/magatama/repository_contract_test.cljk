(ns magatama.repository-contract-test
  (:require [clojure.edn :as edn] [clojure.test :refer [deftest is]]))
(deftest canonical-edn
  (doseq [p ["identity.edn" "manifest.edn" "schema.edn" "dependencies.edn"
             "repository-contracts.edn" "migration.edn"]]
    (is (some? (edn/read-string (slurp p))) p)))
(deftest external-boundary
  (let [c (edn/read-string (slurp "repository-contracts.edn"))]
    (is (= :edn (:canonical-data c)))
    (is (= #{:toml} (get-in c [:external-formats :formats])))))
